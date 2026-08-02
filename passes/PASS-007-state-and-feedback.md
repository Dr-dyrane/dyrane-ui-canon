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

## Contradiction searches required

- My Finance optimistic updates and reconciliation states.
- My Finance dock, Reading Pill and contextual action state ownership.
- iVisit payment-to-tracking handoff.
- iVisit completion and rating recovery.
- iVisit cancellation and destructive-action ownership.
- WetinDey contribution confirmation and freshness states.

## Deliverables

- [x] Open PASS-007.
- [x] Record the initial state hierarchy.
- [x] Record request-scoped transient evidence.
- [x] Record snapshot-before-presentation architecture.
- [ ] Audit complete tracking controller outcomes.
- [ ] Audit rating persistence and recovery.
- [ ] Audit cancellation and destructive transitions.
- [ ] Compare with My Finance optimistic and reconciled state.
- [ ] Write feedback grammar.
- [ ] Run constitutional promotion review.
- [ ] Define implementation and verification contracts.

## Completion gate

PASS-007 remains open until the state hierarchy and feedback grammar have been validated across at least iVisit App and My Finance, contradiction cases are documented, and no proposed rule depends on healthcare-specific lifecycle vocabulary.
