# My Finance — Reading Pill and Stacked Bottom Architecture

- Source product: `Dr-dyrane/planned`
- Evidence commit: `262dea2dd44550ae166e442579b53c40a8de651c`
- Evidence status: source-verified, render review pending
- Promotion level: validated product pattern / cross-product hypothesis
- Primary passes affected: navigation, interaction, motion, feedback, responsive topology, accessibility

## Finding

My Finance introduces a distinct bottom-of-viewport composition in which a compact live-reading surface sits above the persistent navigation/action dock.

This is not one large toolbar and it is not a badge attached to navigation.

It is a layered grammar:

```text
viewport content
        ↓
Reading Pill
        ↓
Dock Pill
        ↓
contextual action orb or action pill
```

Each layer answers a different question:

- Reading Pill: **What is happening now?**
- Dock Pill: **Where can I go?**
- Contextual action: **What is the most relevant thing I can do?**

The separation is the important contribution. Information, navigation and action are visually adjacent but semantically independent.

## Why “Reading Pill”

“Status pill” is too narrow. Status commonly implies a binary, temporary or categorical state such as online, overdue or complete.

The My Finance surface carries an interpreted reading of the current financial context:

- a named lens (`Stats`);
- the active range;
- a current detail;
- a compact pace sparkline;
- a path into deeper evidence.

It is therefore not merely a status indicator. It is a compressed analytical surface.

### Working definition

> A Reading Pill is a compact, persistent interpretation of the product’s current truth layer. It communicates enough live context to remain useful in its smallest posture and opens a deeper evidence surface when activated.

## Source evidence

The compact `ActivityStatsDockTrigger` was refined so compression does not reduce the surface to an icon or generic label.

The compact variant retains:

- `Stats` plus the active range label;
- a second-line detail;
- a compact `MiniPace` sparkline;
- tighter, variant-owned spacing;
- semantic focus and selection behavior.

The same change adds a governed liquid-interaction treatment to dock items and the contextual action control:

- fine-pointer hover lifts and slightly enlarges the material;
- a radial wash grows from the lower contact edge;
- active press compresses the surface;
- reduced motion removes spatial movement;
- forced-colors mode replaces translucent effects with explicit system highlight colors.

This is meaningful because the interaction feedback changes the material itself rather than layering an unrelated tooltip, glow or detached animation over it.

## Semantic architecture

The bottom system should be understood as three neighboring owners.

### 1. Reading owner

Owns:

- current interpretation;
- timeframe or scope;
- compact trend evidence;
- disclosure into a deeper analytical surface.

Does not own:

- global navigation;
- irreversible actions;
- arbitrary notifications;
- decorative metrics without consequence.

### 2. Navigation owner

Owns:

- destinations;
- current-location state;
- stable route switching;
- persistent product orientation.

Does not own:

- live financial interpretation;
- contextual form submission;
- temporary success/error state.

### 3. Contextual-action owner

Owns:

- the most relevant available action for the current route or context;
- direct press feedback;
- disabled, busy and completion behavior;
- action-specific accessible naming.

Does not own:

- route selection;
- passive status;
- multiple equal-priority actions.

## Visual hierarchy

The Reading Pill must remain visually quieter than the action owner while remaining more informative than a notification badge.

Recommended hierarchy:

1. contextual action — highest action salience;
2. current destination — highest navigation salience;
3. Reading Pill — persistent informational salience;
4. inactive destinations — quiet orientation.

The Reading Pill should not visually compete with the contextual action merely because both are floating surfaces.

## Compactness rule

Compact posture must preserve utility.

Compression may reduce:

- horizontal spacing;
- chart width;
- secondary ornament;
- trailing disclosure affordance when the whole surface is already interactive.

Compression must not remove all of:

- identity;
- scope;
- current reading;
- evidence of change.

A compact analytical surface that becomes only an icon is no longer a Reading Pill. It has become a launcher.

## Motion and material

The source implementation suggests a reusable Dyrane motion principle:

> Feedback should deform the owned material before introducing detached decoration.

For fine pointers:

- hover may lift by approximately one pixel and scale subtly;
- the material wash should originate near the expected contact edge;
- press should return toward the resting plane and compress slightly.

For touch:

- direct press compression is sufficient;
- hover-dependent meaning must not exist.

For reduced motion:

- remove lift, scale and wash travel;
- preserve color, focus and state feedback;
- do not remove semantic distinction.

For forced colors:

- abandon glass fidelity;
- use explicit platform highlight/background/text colors;
- preserve focus, selection and current-destination meaning.

## Accessibility contract

A Reading Pill should expose:

- a concise accessible name;
- current scope or range;
- the key reading in text;
- button semantics if it opens detail;
- selected/expanded state only when those meanings are true;
- a non-chart textual equivalent for trend information.

The sparkline is supporting evidence and should remain hidden from assistive technology when the same trend is already stated in text.

Color, translucency and motion must never be the only carriers of meaning.

## Responsive topology

The composition is strongest when treated as responsive topology rather than fixed stacking.

Possible transformations:

- compact mobile: Reading Pill above Dock Pill, contextual action adjacent or attached as a separate owner;
- wider mobile: Reading Pill may widen while remaining separate from navigation;
- tablet: Reading Pill may move into a dock-adjacent lens or sidebar reading slot;
- desktop: the same reading may become an inspector summary, command-bar reading or persistent analytical lens.

The semantic roles must survive even if the exact vertical stack does not.

## Anti-patterns

Do not:

- merge reading, navigation and action into one undifferentiated bar;
- turn every metric into a floating pill;
- use the Reading Pill as a notification inbox;
- show a chart without a textual reading;
- let the reading obscure page content or critical controls;
- make the compact posture decorative but informationally empty;
- use status colors as the reading’s primary identity;
- attach destructive actions to the same compact surface.

## Promotion assessment

### Strong product-level evidence

- clear semantic separation;
- compact posture retains information;
- interaction and reduced-motion behavior are implemented;
- forced-colors behavior is explicitly handled;
- source tests guard the compact information contract.

### Still required before canon promotion

- rendered review on representative mobile widths;
- thumb-reach and occlusion review;
- dynamic-type and localization stress testing;
- comparison against the pending bottom action pill implementation;
- cross-product validation in at least one non-finance product;
- proof that the pattern remains useful without a sparkline or financial metric.

## Candidate pattern statement

> Separate persistent reading, navigation and contextual action into distinct owners. Keep them spatially related when that improves reach and continuity, but do not collapse their semantics into one control surface.

## Candidate Dyrane terms

- **Reading Pill** — compact interpretation of current product truth;
- **Dock Pill** — persistent destination owner;
- **Action Pill / Action Orb** — current-context action owner;
- **Stacked Bottom Architecture** — coordinated placement of these independent owners near the bottom reach zone.

These names remain provisional until cross-product validation and specification review.