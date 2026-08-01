# PASS-003 — Motion

Status: Active
Confidence: Medium-high for iVisit map system

## Objective

Extract the Dyrane motion model from implementation evidence, distinguish structural motion from decorative animation, and define promotion criteria for a reusable motion specification.

## Current evidence cluster

- `ivisit-app/components/map/useMapSheetShell.js`
- `ivisit-app/components/map/mapSheetShell.gestures.js`
- `ivisit-app/components/map/core/useMapSheetDetents.js`
- `ivisit-app/components/map/views/shared/MapPhaseTransitionView.jsx`
- `ivisit-app/components/map/tokens/mapMotionTokens.js`
- `ivisit-app/components/map/views/tracking/MapTrackingStageBase.jsx`

## Findings

### 1. Structural truth owns motion

The map sheet changes posture by animating one continuous height value. Insets, radii, handle width, glass shape, and content spacing derive from that same value. Ordinary half-to-expanded movement does not use `translateY` as a proxy.

Candidate rule:

> Animate the property that represents the structural change, not a visual substitute for it.

### 2. Preview and commitment are separate

During direct manipulation, the sheet follows the pointer within allowed height bounds. The semantic snap state changes only after release thresholds establish directional intent. Failure to cross a threshold returns the surface to the current detent.

Candidate rule:

> Continuous manipulation may preview state; discrete product state commits only after intent is demonstrated.

### 3. Motion is platform-adaptive but centrally owned

`mapMotionTokens.js` defines shared springs, easing, release distances, velocities, axis-lock ratios, body gesture behavior, scroll-detent behavior, and web cooldowns. Platform variants modify the contract without allowing phase-local magic numbers.

Candidate rule:

> Platforms may differ in interaction physics, but motion ownership remains centralized.

### 4. Phase transition is intentionally subordinate

`MapPhaseTransitionView` uses a short fade plus an eight-point upward settle: opacity 180 ms and translation 220 ms with cubic ease-out. It does not remount or animate the map shell.

Interpretation:

The transition says “content changed inside the same place,” not “you navigated to a new place.”

Risk:

The component currently has no reduced-motion branch and resets on every `phaseKey` change, including identity changes within the same phase.

### 5. Tracking contains a local reduced-motion precedent

Tracking title motion uses `useReducedMotion()`. Under reduced motion, it immediately reaches its final opacity and position and records the transition as completed. This is the strongest current implementation precedent for the map family.

Candidate rule:

> Reduced motion preserves state and hierarchy while removing travel, spring, and staged reveal.

## Initial motion taxonomy

1. **Direct manipulation** — follows input continuously.
2. **Structural settle** — resolves a surface to an allowed posture.
3. **Phase continuity** — indicates content replacement within a persistent shell.
4. **State acknowledgement** — briefly confirms a lifecycle change.
5. **Progress motion** — represents an evolving measured value.
6. **Attention motion** — rare, interruptible, and never the sole status channel.
7. **Dismissal motion** — removes a transient layer or exits the spatial system.

## Gaps

- Shared reduced-motion adapter for shell, detents, and phase transitions.
- Cancellation and interruption semantics for `MapPhaseTransitionView`.
- Measured device verification of spring duration and overshoot.
- One shared progress clock for hero and map marker.
- Accessibility announcements tied to structural settles.

## Promotion gate

Do not promote a motion law until it is compared against My Finance and at least one non-map product.
