# iVisit App — Map Sheet Source Audit

Status: active research
Date: 2026-08-01
Scope: current map sheet shell, detents, gesture ownership, motion, and accessibility
Evidence source: `Dr-dyrane/ivisit-app` main branch

## Executive finding

The active iVisit map surface has a strong interaction architecture but an incomplete accessibility contract.

Its best work is structural:

- sheet height, not translateY, owns ordinary detent movement;
- detent order and allowed postures are centralized;
- scroll, wheel, and direct-handle gestures share semantic snap-state helpers;
- gesture ownership is deliberately separated by presentation and region;
- phase content is insulated from shell choreography;
- shell chrome interpolates continuously as the sheet grows.

Its main weakness is that gesture sophistication is ahead of accessible control sophistication. The visible handle is pressable and has a generous hit target, but the current source does not expose an accessibility role, label, state, hint, or explicit expand/collapse actions. Reduced-motion behavior is also not visible in the shell implementation.

## 1. Shell ownership

`useMapSheetShell` is the current geometry and material owner.

It resolves:

- viewport variant;
- safe-area behavior;
- sheet versus modal/sidebar presentation;
- allowed gesture regions;
- interpolated height;
- corner treatment;
- island insets;
- handle width;
- glass material layers;
- responsive sidebar geometry.

The implementation animates a single `sheetHeightValue` toward the selected detent. Ordinary snap changes therefore preserve bottom anchoring and change the amount of visible sheet rather than moving a fixed-height card through space.

This is a mature form of the Dyrane motion rule:

> Animate the property that represents the actual structural change.

For a bottom sheet changing posture, that property is height. Translation is reserved for dismissal or offscreen movement.

## 2. Continuous chrome interpolation

The shell derives a normalized chrome progression from collapsed through half to expanded.

That progression controls:

- side inset;
- bottom inset;
- top and bottom radii;
- handle width;
- content padding;
- handle spacing.

This means the surface does not merely jump among three style presets. Its material language changes continuously with posture.

Potential canon candidate:

> When a surface changes topology continuously, its chrome should interpolate from the same progress signal rather than switch independently at arbitrary thresholds.

## 3. Direct gesture model

`mapSheetShell.gestures.js` uses vertical-intent detection with:

- activation distance;
- axis-lock ratio;
- release distance;
- release velocity;
- bounded live height;
- spring restoration when no detent change commits.

The live drag updates height directly and clamps it to the minimum and maximum allowed detent heights.

The release path does not infer arbitrary pixel destinations. It chooses the next semantic allowed snap state and delegates the actual state change through `onHandlePress`.

This is important: the gesture manipulates a continuous physical value, but commits a discrete semantic state.

## 4. Scroll and wheel detents

`useMapSheetDetents` separates content browsing from posture changes.

Key safeguards include:

- no mid-scroll snap;
- release-commit behavior;
- top-edge arming;
- meaningful distance and velocity requirements;
- stronger conditions for half-to-collapsed movement;
- wheel accumulation rather than single-event triggering;
- wheel cooldowns;
- reset of scroll position when a detent transition commits;
- sidebar presentations disabling sheet detents entirely.

The hook also allows half-to-expanded transition at the end of genuinely scrollable content, but only when the user has moved enough distance to prove intent.

This is strong evidence for a future interaction law:

> Continuous input may preview a transition, but consequential state changes commit only after user intent is sufficiently clear.

## 5. Gesture ownership

The system explicitly chooses whether the handle, header region, or body region owns the pan responder.

This avoids the common failure where nested scroll views, sheet gestures, buttons, and map gestures all compete for the same pointer sequence.

The architecture also disables these gesture regions for sidebar presentation, acknowledging that a desktop side panel is not simply a large bottom sheet.

Potential canon candidate:

> Gesture ownership is part of component architecture, not an event-handler afterthought.

## 6. Accessibility gap: handle semantics

`MapSheetShell.jsx` renders the grabber inside a `Pressable` with a substantial hit target and `hitSlop`.

However, current source inspection did not find:

- `accessibilityRole`;
- `accessibilityLabel`;
- `accessibilityHint`;
- `accessibilityState`;
- `accessibilityActions`;
- `onAccessibilityAction`;
- explicit announcement of posture changes.

A screen-reader user may therefore encounter an unnamed pressable or may not receive a reliable description of whether the sheet is collapsed, half, or expanded.

Recommended contract:

- role: button or adjustable, depending on platform support;
- label: phase-specific object plus `sheet` where helpful;
- state/value: current posture;
- hint: `Expands details` or `Collapses details`;
- actions: expand and collapse where supported;
- posture changes announced only when they result from user action or materially change available content.

Example semantic model:

```text
Label: Care options
Value: Half expanded
Actions: Expand, Collapse
```

The visual handle itself should remain decorative and hidden from accessibility; the larger pressable owns the semantics.

## 7. Gesture alternatives

Tapping the handle provides one non-drag alternative, which is positive.

But a toggle alone is weaker than explicit expand/collapse actions because:

- its result depends on current posture;
- allowed posture sets vary by phase;
- a user may not know whether activation will expand or collapse;
- switch-control and voice-control users benefit from explicit action names.

Required future evidence:

- whether phase headers expose separate buttons;
- keyboard behavior on web;
- VoiceOver/TalkBack rotor actions;
- switch-control behavior;
- focus retention after posture changes.

## 8. Reduced-motion gap

The shell uses `Animated.spring` for posture changes and interpolates chrome continuously.

No reduced-motion preference check was found in the inspected shell, gesture, or detent files.

This does not prove reduced motion is absent globally, but it means the shell does not visibly own a reduced-motion substitution.

Recommended contract:

- reduced motion should preserve posture change but remove elastic overshoot and prolonged interpolation;
- direct drag remains direct because it tracks the user’s finger;
- release should settle quickly with a critically damped or short timing transition;
- phase changes should use immediate replacement or a minimal crossfade;
- no loss of state or hierarchy is permitted when animation is reduced.

## 9. Motion strengths and risks

### Strengths

- height models the real topology;
- one shared progress signal drives chrome;
- platform motion tokens centralize thresholds and spring behavior;
- Android overshoot is clamped;
- cancelled gestures restore the current detent;
- sidebar behavior is structurally distinct;
- scroll and posture gestures are designed not to fight.

### Risks

- non-native height animation cannot use the native driver;
- continuous glass and radius interpolation may be expensive on lower-end Android devices;
- reduced-motion behavior is not explicit;
- no visible announcement contract accompanies posture change;
- a toggle-only handle may be ambiguous for non-gesture users;
- source-level correctness still requires device testing for nested gesture arbitration.

## 10. Provisional scoring adjustment

For the map sheet subsystem only:

| Dimension | Score | Rationale |
|---|---:|---|
| Structural coherence | 9.5/10 | Clear shell, detent, gesture, phase boundaries |
| Motion coherence | 9/10 | Topology-driven height and shared interpolation |
| Gesture precision | 9/10 | Release commit, axis lock, cooldowns, semantic snap states |
| Responsive transformation | 9/10 | Sheet and sidebar are distinct presentations |
| Accessibility | 5/10 | Large target and tap alternative, but missing explicit semantics and actions |
| Reduced motion | 4/10 | No local evidence of substitution |

## 11. Promotion candidates

### High confidence

- Animate structural truth, not a visual proxy.
- Gesture ownership must be explicit.
- Consequential gesture state commits on demonstrated intent.
- Responsive transformation may disable an interaction model rather than resize it.
- One progress signal should drive a continuous material transition.

### Medium confidence

- Every draggable surface requires a non-drag alternative.
- Surface posture is user-visible state and must be exposed accessibly.
- Reduced motion changes choreography, not information architecture.

## 12. Next audit

1. Inspect `MapPhaseTransitionView` and motion tokens.
2. Inspect map camera padding and viewport-fit ownership.
3. Inspect `MapTrackingStageBase` and `useMapTrackingController`.
4. Build a phase accessibility matrix.
5. Verify header, close, and CTA semantics.
6. Search for global reduced-motion utilities before concluding the gap is product-wide.
