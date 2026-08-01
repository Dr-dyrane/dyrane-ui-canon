# iVisit App Archaeology — Emergency Interaction System

Status: active research
Date: 2026-08-01
Source repository: `Dr-dyrane/ivisit-app`
Audit depth: D3, moving toward D4

## Research question

What interaction ideas originated or materially matured in iVisit App before they were standardized in iVisit Console and semantically formalized in My Finance?

## Evidence window

This pass inspected:

- emergency-related commits from December 2025 through January 2026;
- the January 10 Emergency Screen refactor plan;
- the April 21 map-and-sheet specification and its later archival notice;
- search/header coordination changes;
- real-time tracking, persistence, notification, haptic, and sound work.

## Chronology

### December 25, 2025 — emergency introduced as a product identity

Commit `8d6a3444` added an emergency onboarding vector. At this stage, emergency was still represented largely as a feature and branded entry point rather than a mature spatial system.

### January 8, 2026 — bottom sheet becomes the primary emergency surface

A rapid sequence of commits modified and then explicitly improved `EmergencyBottomSheet.jsx`:

- `e856da83`
- `668548d6`
- `d866198d`

This is the earliest strong evidence in the current history that the emergency experience was consolidating around a persistent lower surface rather than a chain of replacement pages.

The same day, `f62e505d` extracted bed-booking choices and information tiles, while `4663e7c3` introduced ambulance and bed-booking tracking with route and progress visualization.

The design implication is important: selection, commitment, and tracking were being placed into one continuous spatial context.

### January 9, 2026 — state persistence and spatial chrome coordination

Commit `71e4a2bf` added emergency-state persistence, request lifecycle management, completion and cancellation.

Commit `a8947b77` coordinated search focus, sheet expansion, and header visibility. Search focus:

1. locks the header hidden;
2. hides the header;
3. expands the bottom sheet;
4. restores header behavior only after blur.

This is early implementation evidence for a durable Dyrane idea:

> Chrome yields to the active task rather than competing with it.

It is not just responsive styling. Multiple interface regions coordinate around the user's current intent.

### January 9–10, 2026 — persistence becomes real-time product truth

Commit `9a34a4ca` moved emergency requests and responder tracking from local persistence to Supabase, with geospatial queries and real-time location updates.

Commit `b4f7a762` enforced a service-layer architecture and strict database synchronization.

This changed the design responsibility of the interface. The UI was no longer presenting a local simulation as if it were authoritative; state increasingly had to reflect shared system truth.

### January 10, 2026 — modularization exposes the interaction architecture

The Emergency Screen refactor plan (`474270d2`) described a clear separation:

- `EmergencyContext` owns domain and operational state;
- `EmergencyUIContext` owns animation, snapping, search, and interface state;
- map integration owns route and viewport behavior;
- the sheet is expected to react to database lifecycle changes.

The plan also identified race conditions where the UI cleared or changed phase before database writes completed. This is a design issue, not only an engineering issue. A surface that visually completes before system truth is committed lies to the user.

Candidate rule:

> A visual state transition must not outrun the authoritative state transition it claims to represent.

### January 10, 2026 — feedback expands beyond the screen

The notification work established priority-aware feedback across:

- in-app notification state;
- haptics;
- sound;
- real-time subscriptions;
- user preferences.

The priority model distinguished urgent, high, normal, and low events. Later canon work should verify whether the exact mapping survived, but the conceptual contribution is clear:

> Feedback modality should scale with consequence.

This predates the current canon's feedback ladder and provides portfolio evidence for it.

### April 21, 2026 — the map-and-sheet doctrine becomes explicit

The emergency sheet specification states:

- the map remains the spatial truth layer;
- the sheet changes state more often than the route shell;
- each state has one dominant decision;
- glanceable information appears first;
- deeper detail comes through expansion before route replacement;
- authentication and payment arrive late;
- the shell owns shape, motion, blur, and snap behavior;
- content sections own their local inset and density.

This is the clearest early articulation of Dyrane spatial grammar.

## Reconstructed interaction model

```text
Persistent spatial truth
        ↓
Resting or glanceable sheet
        ↓
One current decision
        ↓
Expanded detail without losing context
        ↓
Explicit commitment
        ↓
Live tracking in the same spatial world
        ↓
Completion only after authoritative state agrees
```

## Original contributions versus external influence

### Clearly influenced by Apple Maps and platform sheet conventions

- persistent map with overlaid sheet;
- collapsed, mid, and expanded postures;
- drag handle and detent behavior;
- search-driven sheet expansion;
- preserving spatial context during browsing.

### Distinctly Dyrane adaptations

- map described as reality or spatial truth rather than merely background;
- sheet described as state plus decision;
- late authentication as a trust and urgency choice;
- one dominant decision per emergency phase;
- explicit prohibition against inventing hospital data to fill visual space;
- visible pending feedback held long enough to be perceived;
- UI transition sequencing tied to database authority;
- local layout ownership rules inside one persistent shell.

## Candidate constitutional principles

These remain hypotheses until cross-project validation.

1. **Reality before interface.** Preserve the user's operational or spatial context while the interface changes around it.
2. **One dominant decision per state.** A surface should make its current question obvious.
3. **Progressive commitment.** Exploration, comparison, commitment, tracking, and completion are distinct consequence levels.
4. **Chrome yields to task.** Headers, rails, and navigation should recede when they compete with the active interaction.
5. **Motion preserves topology.** Expansion and transition should explain where detail came from and where it remains.
6. **Feedback scales with consequence.** Visual, haptic, audible, and interruptive feedback should match urgency and reversibility.
7. **The interface must not outrun truth.** Completion visuals wait for authoritative completion.
8. **Do not fabricate visual completeness.** Missing trustworthy data should remain missing or use an honest fallback.
9. **Layout ownership must be explicit.** Shell, section, rail, and content each own distinct spacing and behavior.

## Contradictions and weaknesses

- Early January implementations still used generic card systems, gradients, shadows, and modal consolidation that later Dyrane work would reject or refine.
- A two-second minimum pending state risks becoming artificial latency when applied indiscriminately. The underlying principle is perceptibility, not a universal duration.
- Gesture-first sheet behavior requires explicit non-gesture alternatives and accessibility verification.
- The refactor plan reveals that visual flow and backend truth were not initially synchronized reliably.
- The documentation is unusually strong, but implementation parity must still be verified file by file.

## Relationship to later products

### iVisit Console

The Console inherits iVisit App's truth and consequence concerns, then turns them into fail-closed commands, loading honesty, shared page grammar, and automated gates.

### My Finance

My Finance inherits the same concern for honest state and progressive commitment, then formalizes semantic ownership: entity, fact, action, status, and navigation become distinct systems.

## Provisional conclusion

iVisit App is the strongest known origin of Dyrane interaction philosophy. It does not yet contain the mature visual restraint or semantic registries of My Finance, but it establishes the deeper behavior:

> Keep reality stable, ask one clear question, reveal detail progressively, delay commitment until necessary, and never let the interface claim more certainty than the system possesses.

## Next evidence required

- inspect current `EmergencyBottomSheet` implementation and phase renderer;
- inspect map viewport ownership and marker semantics;
- inspect gesture alternatives and screen-reader behavior;
- inspect the tracking sheet audit and current implementation rules;
- compare the commitment ladder against WetinDey and My Finance;
- determine which January behaviors survived the April–July rewrites.
