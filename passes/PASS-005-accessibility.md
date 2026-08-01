# PASS-005 — Accessibility

Status: Active
Confidence: Medium

## Objective

Treat accessibility as a first-class interaction contract across motion, state, navigation, feedback, and responsive transformation.

## Evidence-backed positives

### Tracking reduced motion

`MapTrackingStageBase` uses `useReducedMotion()`. The title animation resolves immediately under reduced motion while preserving the final state and recording the animation as completed.

### Phase-local posture control

Tracking exposes explicit expand/collapse controls with posture-specific accessibility labels:

- Expand tracking sheet
- Collapse tracking sheet

This is a valid non-gesture alternative for that phase.

### Error and success feedback

Tracking actions surface readable toast feedback for arrival confirmation, sharing fallback, and completion failure. Backend or platform failure is not silently swallowed in these paths.

### Non-color status copy

Tracking models contain stage-keyed copy such as awaiting approval, finding driver, ETA, and arrival state. Color is therefore reinforcement rather than the only information channel.

## Confirmed gaps

### Base sheet handle semantics

The shared `MapSheetShell` handle is pressable and has generous hit slop, but the source inspected does not expose:

- accessibility role
- label
- value/current posture
- hint
- custom expand/collapse actions
- announcement after posture change

A phase-local toggle does not fully repair the shared primitive because not every phase is proven to provide one.

### Shared phase transition reduced motion

`MapPhaseTransitionView` always fades and translates on `phaseKey` changes. No reduced-motion path was found in the component.

### Focus management

The audit has not yet proven:

- focus transfer to a newly entered phase
- focus restoration after close/back
- focus containment for modal presentations
- heading semantics for phase titles

### Live state announcements

The audit has not yet proven announcements for:

- phase change
- payment success/failure
- ambulance arrival
- bed readiness
- request completion
- sheet posture change

### Dynamic type and reflow

Responsive metrics exist, but dynamic text scaling and large-text reflow remain unverified.

## Canonical accessibility contract candidate

Every stateful surface should expose:

1. semantic name
2. current state/value
3. available actions
4. non-gesture alternatives
5. focus destination on entry
6. focus restoration on exit
7. readable pending and error feedback
8. reduced-motion equivalent
9. non-color communication
10. sufficient target geometry

## Initial matrix

| Surface | Gesture alternative | Reduced motion | Focus contract | Live announcement | Status |
|---|---|---|---|---|---|
| Base sheet handle | Partial tap only | Not found | Not found | Not found | Gap |
| Tracking title | N/A | Implemented | Unverified | Unverified | Partial |
| Tracking posture | Explicit toggle | Shell still animated | Unverified | Not found | Partial |
| Phase transition | N/A | Not found | Unverified | Not found | Gap |
| Async tracking actions | Buttons | N/A | Normal button path | Toast feedback | Partial |
| ETA share | Button + fallback | N/A | Normal button path | Toast feedback | Strong |

## Promotion gate

Accessibility rules may be promoted only after source verification in My Finance and at least one desktop-oriented repository.
