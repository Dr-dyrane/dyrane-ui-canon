# iVisit App — Rating Recovery, Completion, and Cancellation Semantics

- Source repository: `Dr-dyrane/ivisit-app`
- Evidence class: active source implementation
- Active pass: PASS-007 — State and Feedback Constitution
- Status: evidence recorded; cross-product validation pending

## Scope

This note records the current iVisit behavior for:

- screen-level rating restoration;
- terminal completion handoff;
- persisted recovery claims;
- rating skip and submit resolution;
- cancellation cleanup;
- arrival acknowledgement;
- responder-owned completion;
- feedback after partial success.

## 1. Persistent consequences live above transient phases

The rating renderer was moved out of `MapTrackingStageBase` and lifted to `MapScreen`.

The defect was architectural rather than visual: when the tracking phase changed, a modal rendered inside the tracking stage unmounted before the user could respond.

The corrected ownership is:

```text
Tracking controller
  owns the completion trigger

Screen-level rating flow
  owns the persistent consequence

Screen root
  owns the renderer lifetime
```

This supports a high-confidence candidate rule:

> A consequence that must survive a phase transition must be owned above the phase that initiated it.

## 2. Recovery claims are written before cleanup

Completion does not immediately discard the trip and hope the rating surface remains mounted.

The controller first commits authoritative completion, then writes a persistent rating recovery claim, then opens the rating state. Cleanup is deferred until the rating is submitted or explicitly skipped.

This order prevents a terminal request from disappearing before the product has secured the next required consequence.

Candidate rule:

> Secure the recoverable consequence before removing the state that produced it.

## 3. Server truth validates persisted presentation state

The rating state may persist locally, but local visibility is not final authority.

The screen-level rating flow validates the atom against loaded visits:

- a visit already rated on the server closes the persisted modal;
- a just-completed in-flow handoff may survive a short query lag when `completionCommitted` is true;
- recovered rating remains visible only while canonical visit lifecycle remains eligible.

This distinguishes persistence from authority:

```text
Local persistence
  preserves continuity

Canonical visit lifecycle
  decides validity
```

Candidate rule:

> Persisted presentation state must be revalidated against authoritative truth before it is restored.

## 4. Recovery is not restricted to the original device

A local recovery claim narrows the recovery search when one exists, but the absence of a claim does not block recovery.

A fresh device may recover a completed, unrated emergency visit from canonical visit truth alone.

This is important because local storage is evidence of an interrupted handoff, not the source of the completion obligation.

Candidate rule:

> Local recovery metadata may accelerate or disambiguate restoration, but canonical unresolved consequences must remain recoverable without it.

## 5. Duplicate rating prevention is an ordering problem

During skip resolution, the flow:

1. resolves the skip against the visit;
2. suppresses same-session rediscovery;
3. removes the in-memory recovery claim;
4. clears the visible rating state;
5. finalizes trip cleanup;
6. refetches authoritative visit state;
7. reports the resolved outcome.

The source comments explicitly note that reversing the claim-removal and cleanup order can reopen the same visit for one render and recreate a duplicate rating surface.

Candidate rule:

> Recovery systems must close every discovery path before removing the state that currently suppresses rediscovery.

## 6. Partial success is reported honestly

Rating submission can succeed while an optional tip fails.

The system does not collapse both operations into a false all-or-nothing result. It reports:

- feedback saved;
- tip still needs attention.

This supports a reusable feedback rule:

> When a compound action partially succeeds, report the committed result and the unresolved remainder separately.

## 7. Cancellation clears presentation only after authoritative success

Ambulance and bed cancellation use a shared base handler.

The authoritative request status is updated first. Trip cleanup runs only when the request operation succeeds, unless an explicit `cleanupOnFailure` policy is supplied.

Therefore a failed cancellation does not silently remove the active trip from local presentation.

Candidate rule:

> Destructive cleanup must follow confirmed authoritative mutation; failure preserves the current truth and its recovery path.

## 8. Completion is responder-owned

The patient-facing completion handler does not manufacture completion.

For ambulance and bed flows, the handler returns a pending result until the authoritative request status is already `completed`.

The UI may acknowledge or continue a completed lifecycle, but cannot create the lifecycle transition merely because the user pressed a completion control.

Candidate rule:

> A participant may acknowledge a lifecycle transition without owning the authority to create it.

## 9. Arrival acknowledgement is separate from arrival truth

Arrival availability is gated by canonical arrival status.

The patient can acknowledge responder arrival only after the request lifecycle already reports `arrived`. A successful acknowledgement updates the matching active trip, refreshes the active-trip query, and emits success haptics.

This yields a clean distinction:

```text
Responder/system arrival
  authoritative lifecycle event

Patient acknowledgement
  secondary confirmation attached to that event
```

Candidate rule:

> Acknowledgement state must not be confused with the event being acknowledged.

## 10. Feedback model refined

The evidence now supports this stronger sequence:

```text
Intent
  ↓
Lifecycle permission
  ↓
Local busy acknowledgement
  ↓
Authoritative operation
  ↓
Outcome classification
  ↓
Persistent consequence secured
  ↓
Cleanup or recovery
  ↓
User feedback
```

The order is intentionally conservative. Presentation cleanup follows truth, while recovery metadata is secured before transient state disappears.

## High-confidence promotion candidates

1. **Persistent consequences must be owned above transient phases.**
2. **Persisted presentation state must be revalidated against authoritative truth.**
3. **Secure recovery before cleanup.**
4. **Destructive cleanup follows confirmed mutation.**
5. **Acknowledgement does not create the event it acknowledges.**
6. **Partial success must remain legible as partial success.**
7. **Canonical unresolved consequences remain recoverable without local metadata.**

## Remaining contradiction searches

- My Finance approval outcomes and recoverable Advisor state.
- My Finance optimistic mutation rollback.
- Payment-to-tracking handoff after app interruption.
- Cancellation failure messaging at the final rendered surface.
- WetinDey contribution confirmation and stale evidence recovery.

## Promotion status

These findings remain validated iVisit patterns. They should not become constitutional law until My Finance confirms that the same ownership and recovery rules apply outside emergency-care lifecycle vocabulary.
