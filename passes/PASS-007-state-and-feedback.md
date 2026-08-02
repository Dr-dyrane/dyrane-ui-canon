# PASS-007 — State and Feedback Constitution

- Status: active
- Opened: 2026-08-01
- Primary evidence source: `Dr-dyrane/ivisit-app`
- Cross-validation source: `Dr-dyrane/planned`
- Depends on: PASS-002, PASS-003, PASS-004, PASS-005, PASS-006

## Objective

Extract a product-independent Dyrane state model that prevents interface state, lifecycle state, derived state and animation state from impersonating authoritative truth.

## Working model

```text
Authoritative state
        ↓
Lifecycle interpretation
        ↓
Derived product reading
        ↓
Presentation state
        ↓
Animation state
```

The arrows describe dependency, not permission to mutate upward.

## Current evidence

### iVisit tracking runtime

The active tracking runtime separates several responsibilities:

- authoritative request and booking records arrive through the active request and stores;
- lifecycle meaning is resolved from canonical request status and lifecycle flags;
- route telemetry is request-key scoped before it can influence the active trip;
- progress is derived from authoritative timestamps, route duration and the current clock;
- view models and action eligibility are built from the resolved snapshot;
- animation consumes derived presentation values but does not write request truth.

The implementation explicitly refuses to let ETA progress manufacture arrival. Arrival is read from canonical request status.

### Request-scoped transient evidence

Live route data may temporarily fill a missing ETA, but only when its `requestKey` matches the active request. The persistent trip value takes precedence once available.

This establishes a candidate rule:

> Transient evidence may bridge incomplete authoritative state only when it is provenance-scoped, non-destructive and automatically subordinate to authoritative recovery.

### Snapshot before presentation

The runtime first creates a lifecycle-aware tracking snapshot, then builds view state and action eligibility from that snapshot. This is preferable to individual surfaces independently interpreting raw status strings.

Candidate rule:

> A complex surface should consume one governed semantic snapshot rather than reconstruct lifecycle meaning at every call site.

### Action eligibility

Actions are derived after the snapshot and view state are resolved. This means availability follows lifecycle truth rather than visual convenience.

Candidate rule:

> The interface may reveal an action only when the lifecycle model says the action is valid; visual prominence cannot create permission.

### Tracking controller outcomes

The tracking controller now provides source-level evidence for a complete feedback sequence:

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

The controller owns orchestration and feedback, not lifecycle truth.

#### Busy ownership

`runBusyAction` attaches pending state to an action key and clears it in `finally`. The bottom action explicitly recomputes from `busyAction`, preventing a stale enabled control during work.

Candidate rule:

> Foreground asynchronous work must remain owned by the action that initiated it and must clear through a guaranteed terminal path.

#### Completion before cleanup

Ambulance and bed completion defer cleanup. After authoritative completion succeeds, the controller persists a rating-recovery claim before opening the follow-up rating state.

Candidate rules:

> A terminal operation must secure its persistent follow-up consequence before transient presentation state is cleaned up.

> Completion and follow-up are separate contracts: follow-up failure must not undo committed lifecycle truth, and recovery must reconstruct the follow-up.

#### Destructive permission

Cancellation handlers only enter the destructive-action model when lifecycle policy permits cancellation. A destructive control is therefore the visible end of lifecycle permission, not a local dismissal affordance.

#### Cross-surface command safety

Header action requests carry an execution identity, are rejected when already handled, are revalidated against current policy, and are then consumed.

Candidate rule:

> Cross-surface action requests must carry identity, be revalidated at the destination and be consumed idempotently.

#### Intent-preserving fallback

ETA sharing distinguishes user cancellation from system failure and falls back to clipboard only when sharing is unavailable. The fallback reports its actual outcome.

Candidate rule:

> Preserve user intent through the nearest honest fallback without pretending the fallback is equivalent to the preferred capability.

## Feedback model under investigation

```text
Intent
  ↓
Local acknowledgement
  ↓
Authoritative operation
  ↓
Resolved outcome
  ↓
Persistent consequence or recovery
```

Feedback must remain attached to the action or state change that produced it.

## Candidate laws under review

1. **The interface must not outrun authoritative state.**
2. **Animation never owns truth.**
3. **Presentation state cannot grant lifecycle permission.**
4. **Transient evidence must carry provenance.**
5. **One semantic snapshot should govern one complex surface.**
6. **Persistent consequences must outlive transient phases.**
7. **Recovery is part of the primary interaction contract, not an afterthought.**
8. **Foreground work remains attached to its initiating action.**
9. **Terminal operations secure follow-up recovery before cleanup.**
10. **Cross-surface commands require identity and idempotent consumption.**
11. **User cancellation is not system failure.**
12. **Fallbacks preserve intent without fabricating equivalence.**

## Contradiction searches required

- My Finance optimistic updates and reconciliation states.
- My Finance dock, Reading Pill and contextual action state ownership.
- iVisit payment-to-tracking handoff.
- iVisit screen-level rating recovery.
- iVisit cancellation failure feedback and confirmation semantics.
- WetinDey contribution confirmation and freshness states.

## Deliverables

- [x] Open PASS-007.
- [x] Record the initial state hierarchy.
- [x] Record request-scoped transient evidence.
- [x] Record snapshot-before-presentation architecture.
- [x] Audit complete tracking controller outcomes.
- [x] Audit rating-claim persistence before follow-up presentation.
- [x] Audit cancellation and destructive-action policy ownership.
- [ ] Audit screen-level rating restoration, close, skip and submit.
- [ ] Audit payment-to-tracking recovery.
- [ ] Compare with My Finance optimistic and reconciled state.
- [ ] Write feedback grammar.
- [ ] Run constitutional promotion review.
- [ ] Define implementation and verification contracts.

## Completion gate

PASS-007 remains open until the state hierarchy and feedback grammar have been validated across at least iVisit App and My Finance, contradiction cases are documented, and no proposed rule depends on healthcare-specific lifecycle vocabulary.
