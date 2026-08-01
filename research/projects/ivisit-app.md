# iVisit App — Structured Audit

- Repository: `Dr-dyrane/ivisit-app`
- Product family: emergency healthcare / map-first mobile product
- Platform: Expo React Native with web/PWA support
- Audit depth: D2, advancing toward D3
- Canon role: spatial topology, staged commitment, sheet grammar, urgency feedback
- Status: active research

## Provisional thesis

iVisit App is the strongest portfolio evidence for a map-first Dyrane grammar. Its central contribution is not visual map styling. It is the separation of spatial truth, interaction state, and commitment.

The product repeatedly expresses the same doctrine:

- the map remains the persistent reality layer;
- the sheet carries the current state and decision;
- the route shell changes less often than sheet content;
- each phase should expose one dominant decision;
- deeper detail should be revealed through expansion before route replacement;
- authentication and payment arrive near commitment rather than blocking exploration.

## Evidence lineage

The archived emergency-sheet specification records that it originated on 2026-04-21 and was archived on 2026-05-19 after later implementation contracts superseded it. This makes it earlier than the July iVisit Console borderless conversion and the late-July My Finance semantic-registry work.

This is important because it establishes that several Dyrane principles existed before the later visual canon:

- persistent shell;
- progressive disclosure by sheet detent;
- one dominant action per state;
- late commitment;
- decision-specific copy;
- map as truth rather than decoration;
- foreground action feedback as an explicit contract.

## Core topology

```text
map = spatial truth
sheet = state + decision
header = session-level chrome
route = major context boundary
```

The sheet changes more frequently than the route. This preserves spatial continuity while the task progresses.

### Canon candidate

> Preserve the user's reality layer while changing the decision layer whenever the domain has a stable spatial or object context.

This should not become a universal rule. It is appropriate for maps, canvases, media, records, and workspaces where context loss is expensive.

## Detent grammar

The emergency sheet defines three semantic postures rather than merely three heights.

### Collapsed

Purpose:

- preserve map visibility;
- confirm current state;
- offer rapid re-entry;
- avoid long forms or competing actions.

### Mid

Purpose:

- act as the primary phone decision surface;
- show one title, one support fact, one primary action, and a quiet secondary action;
- open most phases here.

### Expanded

Purpose:

- reveal lists, search, alternatives, and editable detail;
- preserve the same shell and task identity;
- increase information density without pretending to be a separate application.

### Canon candidate

> Responsive or layered states must be named by user purpose, not only by pixel height.

A detent is therefore a semantic mode, not a numeric coordinate.

## Sheet anatomy

The documented anatomy is:

1. state label;
2. decision title;
3. confidence or trust line;
4. primary action;
5. secondary action;
6. optional expandable detail.

This reveals an early Dyrane hierarchy pattern:

```text
state
→ decision
→ trust
→ action
→ detail
```

The sheet copy favors explicit consequence over generic progression:

- `Use this location` rather than `Continue`;
- `Use this hospital` rather than `Continue`;
- `Confirm and dispatch` rather than `Submit`;
- `Add details` rather than `Sign up`.

### Canon candidate

> Primary-action copy should name the decision or consequence whenever space permits.

## Commitment ladder

The Explore/Intent phase explicitly refuses to look like:

- a hospital picker;
- pricing;
- dispatch confirmation;
- authentication.

It asks only:

- where should help start;
- what type of help is needed.

This establishes a commitment ladder:

```text
explore
→ express intent
→ compare or choose
→ add necessary details
→ understand cost
→ authenticate when required
→ commit
→ track
```

### Canon candidate

> Do not request irreversible commitment data before the user has enough context to decide.

## Feedback doctrine

The specification contains an unusually explicit foreground-action feedback contract:

- every submit, resend, verification, payment, commitment, or route-changing network action must show immediate pressed or pending feedback;
- successful calls that complete too quickly may hold the pending affordance long enough to remain perceptible;
- backend error codes must be normalized into readable user-facing language;
- passive background hydration should not receive artificial delay.

The historical default perceptibility window was 2000 ms. That numeric value is product-specific and should not be promoted without testing. The deeper principle is stronger:

> A technically successful action can still fail experientially when the state transition erases acknowledgement before the user can perceive it.

This adds an important dimension to Dyrane feedback:

```text
system response time ≠ perceived acknowledgement time
```

## Local ownership

The sheet contract assigns responsibilities precisely:

- shell owns shape, blur, motion, and snap behavior;
- ordinary content sections own their horizontal insets;
- edge-to-edge rails own their own internal padding;
- content does not depend on accidental parent padding.

This anticipates the later My Finance sheet-body ownership rules.

### Historical link

The portfolio appears to evolve as follows:

1. iVisit App documents layout ownership conceptually for sheet shells and content.
2. iVisit Console turns page grammar into shared components and hardgates.
3. My Finance enforces component-owned sheet padding and semantic surface grammar.

This is a stronger lineage than saying My Finance invented ownership in isolation.

## Identity behavior

The app uses several identity mechanisms depending on object type:

- user avatar;
- hospital image card;
- map marker;
- icon-first intent action;
- profile or guest placeholder.

This is evidence against making Icon Orb universal.

### Canon candidate

> Identity must precede content, but the identity primitive must match the object: image for a place when trusted imagery matters, avatar for a person, pin for a location, orb for a symbolic entity, glyph for a destination.

## Map truth and fake-data prohibition

The expanded hospital rail explicitly prohibits injecting fake names, distances, ETA, bed counts, or placeholder hospital records merely to fill the composition. The rail and modal list must consume the same collection to avoid contradictory counts.

This supports a broader Dyrane principle:

> Visual completeness must never create parallel truth.

A sparse but honest surface is preferable to a composition completed with invented operational data.

## Responsive topology

The same persistent shell can move between collapsed, mid, and expanded states while preserving:

- search;
- current location;
- chosen intent;
- nearby-care context;
- profile access;
- map continuity.

The layout changes task density rather than merely scaling components.

## Risks and unresolved questions

- The archived spec may differ from the current production implementation.
- A 2000 ms minimum pending display may feel unnecessarily slow in lower-stakes flows.
- Too much sheet persistence can trap the user in an over-complex single route.
- Image-first hospital identity depends on media quality and truthfulness.
- The map-first grammar should not be copied into products where spatial context is not primary.

## Provisional scoring

| Dimension | Score | Confidence |
|---|---:|---|
| Structural coherence | 18/20 | Medium-high |
| Information hierarchy | 14/15 | Medium-high |
| Interaction grammar | 14/15 | High |
| State and feedback completeness | 9/10 | High in documentation |
| Responsive transformation | 10/10 | High |
| Reusable architecture | 7/10 | Medium |
| Visual restraint | 8/10 | Medium |
| Accessibility | 3/5 | Low-medium pending code audit |
| Motion coherence | 4/5 | Medium-high |
| Product intelligence and trust | 5/5 | High |
| **Provisional total** | **92/100** | Documentation-weighted; implementation audit pending |

This score is intentionally not a final portfolio ranking. The documentation is exceptionally strong, but code and rendered surfaces still require verification.

## Promotion candidates

- Preserve the stable truth layer while changing the decision layer.
- Name layered states by purpose, not dimensions.
- One dominant decision per state.
- Delay commitment until context is sufficient.
- Action copy names consequence.
- Perceived acknowledgement is a design responsibility.
- Layout ownership must be explicit.
- Visual completeness never justifies parallel truth.
- Identity mechanism follows object type.

## Next inspection

- Current `MAP_SCREEN_IMPLEMENTATION_RULES_V1.md`.
- Tracking sheet audit and live tracker.
- Actual sheet controller and snap implementation.
- Reduced-motion and gesture alternatives.
- Screen-reader naming for map and sheet actions.
- Map marker and hospital media fallback implementations.
