# iVisit App — Tracking State Runtime

- Repository: `Dr-dyrane/ivisit-app`
- Primary source: `components/map/views/tracking/useMapTrackingRuntime.js`
- Evidence status: source-level
- Promotion status: hypothesis / validated pattern candidate

## Why this source matters

The tracking runtime is where iVisit converts several kinds of evidence into one user-facing journey:

- active emergency request;
- active ambulance trip;
- active bed booking;
- pending approval;
- lifecycle status;
- route telemetry;
- elapsed time;
- triage progress;
- action eligibility;
- visual progress.

It is therefore a useful test of whether Dyrane UI distinguishes truth from representation.

## State ownership map

```text
Server and persistent records
  active request / trip / booking / approval
        ↓
Canonical lifecycle status
  pending / active / arrived / completed
        ↓
Request-scoped transient telemetry
  route duration / coordinates / telemetry health
        ↓
Derived runtime snapshot
        ↓
View state and action eligibility
        ↓
Surface copy, progress, tone and motion
```

## Finding 1 — ETA cannot manufacture arrival

The runtime comments and implementation make an explicit distinction:

- pending approval may be supplied by the lifecycle machine;
- arrival is resolved from canonical request status;
- computed ETA progress is not allowed to declare arrival.

This is a strong example of the interface refusing to outrun truth.

A progress bar may reach its end because of time estimation drift. That does not authorize the interface to represent the ambulance as arrived.

## Finding 2 — transient telemetry is provenance-scoped

The route-info atom is not accepted globally. The runtime derives a request key and uses live route information only when the telemetry key matches the active request.

This prevents stale route data from a prior trip from entering the current journey.

The live duration may temporarily provide a missing ETA, but only as a fallback. Once the persistent trip has a valid ETA, the persistent value wins.

This establishes three constraints for transient evidence:

1. it must identify the subject it belongs to;
2. it must not overwrite recovered authoritative truth;
3. it must be safe to discard.

## Finding 3 — one semantic snapshot governs the surface

The runtime builds `trackingSnapshot` before deriving action eligibility and presentation state.

That snapshot receives:

- active request objects;
- route information;
- telemetry health;
- arrival and pending meaning;
- progress.

Actions and surfaces do not each independently infer the journey from raw records.

This supports a reusable architecture:

```text
raw records
  ↓
semantic snapshot
  ↓
policy + view model
  ↓
rendering
```

## Finding 4 — action eligibility follows lifecycle meaning

The runtime derives action eligibility only after it has resolved:

- tracking kind;
- lifecycle snapshot;
- request status;
- computed trip state;
- triage completeness;
- pending approval identity.

The interface therefore does not decide that an action is available merely because a button would be useful in the layout.

## Finding 5 — progress has separate meanings

The implementation contains several progress concepts:

- ambulance trip progress;
- route visual progress;
- bed booking progress;
- triage completion progress.

These are not interchangeable.

`routeVisualProgress` is explicitly clamped and corrected by lifecycle status. For example, an in-progress dispatch state may show zero route progress, while arrived and completed resolve to one.

This means a progress value is a reading of a specific process, not a universal status percentage.

## Finding 6 — the clock is derived input, not authority

The runtime advances `nowMs` every second so time-based readings can update. The clock affects remaining time and derived progress, but it cannot independently mutate lifecycle truth.

This distinction is crucial:

> Time can change a reading; it cannot complete an authoritative operation by itself unless the domain contract explicitly grants it that authority.

## Risks and contradictions

### Multiple status sources

The runtime receives lifecycle flags while also reading raw status fields. This is understandable during migration, but creates a risk that two layers can disagree.

The canon should prefer one explicit semantic adapter at the boundary and prevent downstream components from choosing whichever source is convenient.

### Derived-progress drift

The runtime carefully reconciles route telemetry and trip state, but any duplicated progress computation elsewhere can still drift. Earlier tracking audits already found hero and marker progress being calculated separately.

### One-second updates

A one-second state tick is reasonable for tracking, but surfaces must avoid announcing every derived change to assistive technology. Visual freshness and auditory interruption require separate policies.

## Promotion candidates

### Candidate A

> The interface must not outrun authoritative state.

Confidence: high within iVisit; awaiting My Finance validation.

### Candidate B

> Transient evidence may bridge missing truth only when scoped to the same subject and subordinate to authoritative recovery.

Confidence: high within iVisit; likely generalizable.

### Candidate C

> Complex surfaces consume governed semantic snapshots rather than interpreting raw records independently.

Confidence: high; implementation-ready.

### Candidate D

> Action availability is lifecycle policy, not presentation policy.

Confidence: high; awaiting cross-product contradiction search.

### Candidate E

> Progress values are process-specific readings and must not silently stand in for lifecycle state.

Confidence: high.

## Next source cluster

- `useMapTrackingController.js` completion path;
- rating recovery and persistent consequence handling;
- cancellation and destructive action policy;
- `mapTracking.actions.js`;
- `mapTracking.snapshot.js`;
- `mapTracking.model.js`;
- payment-to-tracking recovery path.
