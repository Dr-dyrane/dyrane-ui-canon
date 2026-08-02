# iVisit App — Tracking Controller State and Feedback Audit

- Source repository: `Dr-dyrane/ivisit-app`
- Source files: `components/map/views/tracking/useMapTrackingController.js`, related tracking model and rating helpers
- Research status: source-level evidence
- Affected passes: PASS-003 Motion, PASS-004 Interaction, PASS-005 Accessibility, PASS-006 Navigation, PASS-007 State and Feedback

## Purpose

This audit traces how the active tracking controller translates lifecycle permission into available actions, how foreground work owns busy state, and how completion is made recoverable before the interface leaves tracking.

## Controller position in the state hierarchy

The controller does not decide whether a trip is arrived, complete, cancellable, or eligible for a companion service. It receives a governed `trackingSnapshot` and derives an `actionSurfacePolicy` from it.

```text
Authoritative records
        ↓
Lifecycle-aware tracking snapshot
        ↓
Action-surface policy
        ↓
Action models
        ↓
Rendered controls and feedback
```

This is a critical boundary. The controller owns orchestration and feedback; it does not own lifecycle truth.

## Busy state belongs to the initiating action

`runBusyAction(key, handler)` records the active action key, awaits the operation, and clears the key in `finally`.

The result is local, specific and self-clearing:

- the initiating action can become disabled or show progress;
- unrelated surfaces do not need to invent a global loading state;
- failure cannot strand the interface in a permanent pending presentation;
- `bottomAction` explicitly depends on `busyAction`, preventing a stale enabled state while work is active.

### Candidate rule

> Foreground asynchronous work must remain owned by the action that initiated it and must clear through a guaranteed terminal path.

## Outcome feedback is consequence-specific

Arrival confirmation reports explicit success or failure. A rejected arrival does not advance the surface and communicates the operation failure.

ETA sharing preserves user intent through a platform fallback chain:

1. attempt the native share surface;
2. treat user cancellation as cancellation, not failure;
3. fall back to clipboard when sharing is unavailable;
4. report whether clipboard fallback actually succeeded.

### Candidate rule

> Feedback should describe the resolved consequence, not merely acknowledge that input was received.

### Candidate rule

> When the preferred platform capability is unavailable, preserve the user's intent through the nearest honest fallback and report the fallback outcome.

## Completion is separated from cleanup

Ambulance and bed completion call their authoritative completion handlers with `deferCleanup: true`.

Only after completion is accepted does the controller:

1. persist a rating-recovery claim;
2. clear stale recovered rating state;
3. open a rating state marked `completionCommitted: true`.

This sequence prevents presentation cleanup from erasing the persistent consequence before the follow-up interaction has been secured.

```text
Commit completion
        ↓
Persist recovery claim
        ↓
Open follow-up rating state
        ↓
Cleanup may occur later
```

### Candidate rule

> A terminal operation must secure its persistent follow-up consequence before transient presentation state is cleaned up.

### Candidate rule

> Completion and follow-up are separate contracts: failure of the follow-up surface must not undo a committed lifecycle transition, and recovery must be able to reconstruct the follow-up.

## Recovery is part of the primary path

The rating claim is written before the rating UI is opened. This means recovery is not a later patch for an edge case; it is established as part of normal completion.

The controller also separates ownership:

- the tracking controller opens rating state;
- a screen-level rating flow owns close, skip and submit;
- recovered state is maintained separately from the currently open rating state.

This is evidence for an ownership rule:

> The layer that initiates a persistent consequence may open its follow-up, but lifecycle-complete follow-up management belongs to a stable owner that survives phase replacement.

## Destructive actions are policy-gated

Cancellation handlers are only supplied to the destructive-action model when `actionSurfacePolicy.canCancel` is true.

This prevents the view model from rendering a destructive action merely because a handler exists. Permission is derived from lifecycle policy first.

The controller distinguishes:

- pending approval cancellation;
- ambulance trip cancellation;
- bed booking cancellation.

Each retains the relevant authoritative transition instead of collapsing all destructive behavior into a local dismissal.

### Candidate rule

> A destructive control is the visible end of lifecycle permission, not a local escape hatch.

## Header actions are idempotently consumed

Header action requests carry a `requestedAt` identity. The controller records the last handled identity and refuses to execute the same request twice.

It also resolves the action through current policy before invoking it, then consumes the request.

### Candidate rule

> Cross-surface action requests must carry an execution identity, be revalidated at the destination, and be consumed idempotently.

## Action composition

The controller builds separate action classes:

- primary action;
- secondary actions;
- destructive action;
- middle actions;
- bottom action;
- header-triggered action resolution.

These models are assembled from the same lifecycle policy and busy state. The surface therefore does not independently decide what is primary, destructive or currently disabled.

### Candidate rule

> One governed action model should coordinate prominence, permission, progress and placement across every representation of the same operation.

## State and feedback model supported by this audit

```text
Intent
  ↓
Lifecycle permission check
  ↓
Local action acknowledgement
  ↓
Authoritative operation
  ↓
Resolved success, failure or cancellation
  ↓
Persistent consequence secured
  ↓
Presentation transition or recovery
```

No visual transition is permitted to substitute for the authoritative operation.

## Promotion candidates

High confidence within iVisit:

1. The interface must not outrun authoritative state.
2. Presentation cannot grant lifecycle permission.
3. Foreground work remains attached to its initiating action.
4. Persistent consequences must be secured before transient cleanup.
5. Recovery belongs to the primary interaction contract.
6. Cross-surface commands require identity, revalidation and idempotent consumption.
7. User cancellation is not system failure.
8. Fallbacks must preserve intent without pretending equivalence.

Cross-product validation is still required before promotion to Canon or Law.

## Open questions

- Does pending-request cancellation provide explicit failure feedback before clearing local pending state?
- How does the screen-level rating flow recover claims after process death or navigation?
- Are destructive actions confirmed consistently across platforms?
- Do screen readers receive busy, completion and failure changes at the action owner?
- Does My Finance use the same completion-before-cleanup contract for optimistic mutations and approvals?

## Next evidence

1. `mapTracking.rating` and screen-level `useTrackingRatingFlow`.
2. `useEmergencyHandlers` completion and cancellation semantics.
3. payment-to-tracking recovery documents and active implementation.
4. My Finance action-pill busy, approval and recoverable-outcome contracts.
