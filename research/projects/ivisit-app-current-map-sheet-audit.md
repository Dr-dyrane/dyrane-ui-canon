# iVisit App — Current Map Sheet System Audit

Status: Active research
Date: 2026-08-01
Source repository: `Dr-dyrane/ivisit-app`
Audit depth: D3, current implementation plus active architecture documents

## Executive finding

The legacy `EmergencyBottomSheet` is historically important, but it is no longer the correct unit of analysis for the current experience. The active `/map` system has evolved into a persistent shell architecture composed from:

- `MapSheetOrchestrator` for phase routing;
- phase-specific orchestrators and stages;
- shared shell and body-scroll primitives;
- tokenized detent and motion behavior;
- a persistent map beneath the sheet;
- independent tracking, lifecycle, and UI state layers.

The present system is therefore better described as a **spatial state machine rendered through a persistent sheet**, not a large bottom-sheet component.

## 1. Current implementation anatomy

### 1.1 Phase registry

`components/map/core/mapSheet.constants.js` defines a closed phase vocabulary covering:

- explore and location intent;
- search;
- hospital list and hospital detail;
- service detail;
- care history and visit detail;
- ambulance and bed decisions;
- commitment details, triage, authentication, and payment;
- tracking;
- provider list and provider detail.

The same module defines the three sheet postures:

- collapsed;
- half;
- expanded.

It also owns ordered movement between allowed postures and centralized height derivation. This is materially stronger than phases hard-coding local heights or inventing their own gesture ladders.

### 1.2 Orchestrator role

`MapSheetOrchestrator` receives the active phase, snap state, product data, flow callbacks, tracking state, and selection state. It then delegates to a phase-specific orchestrator and wraps phase output in `MapPhaseTransitionView`.

This structure has three important consequences:

1. The persistent shell can remain conceptually stable while phase content changes.
2. Phase components do not own global navigation truth.
3. The transition primitive can communicate continuity without remounting the map.

The orchestrator is broad and carries a large prop surface. That is acceptable as an integration boundary, but it creates a risk of becoming a parallel application controller. The canon should prefer explicit typed phase payloads over indefinitely growing optional props.

## 2. Phase renderer

### Strengths

- Phase names are explicit rather than inferred from unrelated booleans.
- Each phase receives only the product data and actions it needs through an orchestrator boundary.
- Commitment phases force expanded geometry, correctly distinguishing a consequential form from a casual browse posture.
- Phase changes use a small opacity/translation transition rather than replacing the shell or map.
- Transition keys include phase and, where relevant, entity identity, preserving meaningful replacement behavior.

### Risks

- A large `switch` is clear today but may become difficult to reason about as phases and callbacks grow.
- Optional callbacks with no-op defaults can hide missing wiring. Consequential actions should fail loudly in development.
- The phase registry includes `COMMIT_AUTH`, but implementation parity must be checked to ensure every declared phase has a concrete renderer and transition contract.
- Phase-specific allowed snap states should be explicit data, not only implicit in each stage.

### Canon candidate

> A persistent surface may render many phases, but every phase must have an explicit name, payload contract, allowed postures, dominant decision, entry conditions, and exit consequences.

## 3. Map viewport ownership

The strongest architectural decision remains that the map is not decorative background. It is the continuing spatial truth layer.

The sheet owns:

- task state;
- decision content;
- editable detail;
- commitment;
- tracking controls.

The map owns:

- location;
- selected place;
- nearby options;
- route geometry;
- responder movement;
- spatial consequence.

The sheet shell owns the geometry needed to keep both readable. Sheet height is centralized, and active architecture guidance requires responsive metrics to derive surface geometry rather than allowing each child to establish an independent breakpoint system.

### Viewport contract

A valid implementation should maintain:

- map camera padding derived from live sheet geometry;
- the selected or active spatial subject inside the unobscured viewport;
- no independent phase-level camera padding constants;
- no route remount when a sheet phase changes;
- explicit ownership when a phase temporarily recenters or fits a route.

### Current concern

The architecture documents establish ownership doctrine, but rendered verification is still needed to prove every phase respects the same live sheet-height signal. Source architecture alone cannot prove that markers, routes, and user position remain visible at every device size.

## 4. Gesture alternatives and detents

The active system has substantially improved over simple raw-offset snapping.

Current doctrine includes:

- release-commit rather than accidental mid-scroll snapping;
- distance and velocity gates;
- platform-specific cooldowns;
- stronger web wheel accumulation thresholds;
- Android body collapse only when content begins at the top edge;
- one explicit RNGH gesture path instead of competing responder systems;
- live sheet-height growth while the bottom remains anchored;
- `translateY` reserved for dismissal rather than ordinary detent movement;
- shared motion tokens instead of phase-local magic numbers.

This is strong interaction architecture.

### Accessibility gap

A drag handle is not sufficient as the only means of changing sheet posture. Every gesture-controlled posture change needs a non-gesture alternative:

- handle tap to step upward or toggle;
- explicit close or back controls;
- keyboard commands on web where appropriate;
- screen-reader adjustable actions or clearly labelled expand/collapse buttons;
- no essential action requiring a precise swipe.

The constants module supports deterministic stepping, which is a good foundation, but the audit has not yet proved that every rendered phase exposes those alternatives accessibly.

### Canon candidate

> Gestures accelerate interaction; they never own exclusive access to a state change.

## 5. Tracking architecture audit

The tracking system uses five distinct state layers:

1. Supabase realtime as server truth;
2. TanStack Query for synchronized server data;
3. Zustand for persistent active-trip state;
4. XState for lifecycle meaning;
5. Jotai for local map and sheet UI state.

This architecture is sophisticated, but its value depends on respecting ownership boundaries.

### Strong decisions

- Lifecycle flags belong to XState rather than scattered string comparisons.
- Persistent active trip data belongs outside a phase component.
- Tracking is capable of reopening after hydration rather than existing only as a transient route.
- Tracking progress, responder route, arrival, completion, and rating are treated as one continuous journey.

### Historical defects that reveal canonical rules

The tracking audit identified several truth-boundary failures:

- tracking did not always auto-open after cold-start hydration;
- payment-to-tracking depended on one timing-sensitive signal;
- history resume could attempt tracking for an item that was not the active trip;
- rating UI was mounted inside the tracking phase and could disappear when the phase changed;
- hero progress and map marker movement could derive progress independently and drift.

These defects support four general rules:

1. **Lifecycle meaning outranks raw record presence.**
2. **Critical handoffs need a primary transition and an idempotent recovery path.**
3. **Persistent consequences must render above transient phases.**
4. **One journey should have one progress signal.**

## 6. Accessibility behavior

### Existing strengths

- Shared close-control geometry improves predictability.
- The architecture distinguishes focus-driven expansion from incidental snap changes.
- Keyboard dismissal is tied to collapsing the search state.
- Search does not autofocus when restored to half posture.
- Phase titles and actions are intended to remain concise and state-specific.
- Shared primitives make consistent labels and target sizes achievable.

### Gaps requiring source and rendered verification

The current research has not yet proven consistently across every phase:

- accessible names for icon-only close, profile, map, and sheet controls;
- `accessibilityRole` and state on selected cards and segmented choices;
- announcements for phase changes, pending actions, payment success, arrival, and completion;
- screen-reader alternatives for sheet detent gestures;
- focus transfer when phase content changes;
- focus restoration when closing a detail phase;
- logical order when a visual hero overlaps the sheet body;
- reduced-motion behavior for sheet growth, phase transitions, progress, and pulsing states;
- dynamic-type resilience at half and expanded detents;
- minimum target sizes on map markers and compact collapsed controls;
- non-color communication for tracking status and urgency.

### Required implementation contract

Every map phase should declare:

- screen-reader title;
- initial focus target;
- focus return target;
- live-region events;
- selected/expanded/busy states;
- gesture alternatives;
- reduced-motion substitution;
- dynamic-type overflow behavior.

## 7. Current assessment

| Dimension | Assessment |
|---|---|
| Persistent topology | Excellent |
| Explicit phase architecture | Strong |
| Snap and gesture engineering | Strong |
| Viewport ownership doctrine | Strong, rendered proof pending |
| Tracking truth architecture | Strong but historically timing-sensitive |
| Feedback design | Strong conceptually |
| Accessibility completeness | Incomplete evidence; likely uneven |
| Reduced motion | Insufficiently proven |
| Agent/engineer legibility | Good, weakened by broad prop surface |

## 8. Promotion candidates

High-confidence candidates:

- Preserve the primary truth layer while secondary surfaces change.
- Phase changes should alter state without casually destroying spatial context.
- Sheet posture belongs to the shell; phase content should not invent detent mechanics.
- A consequential phase may constrain available postures.
- Lifecycle meaning should come from a canonical state machine.
- Critical transitions require an idempotent recovery path.
- Persistent consequences render above transient phase content.
- One journey has one progress signal.

Medium-confidence candidates pending rendered and accessibility proof:

- Release-commit detents are the preferred custom-sheet gesture model.
- Bottom-anchored height interpolation should replace translate-based lifting.
- Every phase transition should use a small continuity animation.

## 9. Next verification work

1. Inspect `useMapSheetShell`, `useMapSheetDetents`, and `mapSheetShell.gestures` directly.
2. Inspect the active map camera-padding and viewport-fit hooks.
3. Inspect all shared icon-button and handle primitives for accessibility names and roles.
4. Inspect `MapTrackingStageBase` and `useMapTrackingController` against the historical audit.
5. Verify whether rating rendering has been lifted above the tracking phase.
6. Verify reduced-motion handling in map motion tokens and phase transitions.
7. Build a phase-by-phase accessibility matrix.
