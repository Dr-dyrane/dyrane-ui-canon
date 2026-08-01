# My Finance Identity Architecture

Status: validated pattern candidate  
Source product: `Dr-dyrane/planned`  
Pass relationship: PASS-001 input to future PASS-003  
Authority: research, not final canon

## Finding

My Finance does not use leading icons as decoration. It implements a governed identity architecture in which financial entities, facts and actions resolve through controlled semantic registries before they are rendered by a shared circular primitive.

The strongest candidate rule is:

> Identity precedes content, but identity must describe what a thing is—not what state it is in, where it navigates, or how urgent it currently feels.

## Why the Icon Orb is exceptional

The Icon Orb is visually small but architecturally significant. It unifies five concerns that are usually scattered across screens:

1. **Recognition** — a user can classify the row before reading every word.
2. **Consistency** — the same account, category, fact or action retains the same visual identity across contexts.
3. **Restraint** — color is concentrated in a compact identity locus instead of washing entire cards or rows.
4. **Accessibility** — glyph choice carries the distinction when color is unavailable.
5. **Governance** — feature screens consume identities instead of inventing local icon/color combinations.

The result is a table and list language that feels alive without turning the whole application into a category-colored dashboard.

## Architecture

```text
stored semantic data
        ↓
closed identity resolver
        ↓
{ iconKey, toneKey }
        ↓
semantic wrapper (AccountOrb, FactOrb, ActionOrb, etc.)
        ↓
IconOrb rendering primitive
        ↓
consistent size, shape, tone and accessibility behavior
```

The crucial move is that screens do not normally choose a tone beside a button or row. The registry owns that choice.

## Primitive contract

`IconOrb` accepts only:

- child glyph;
- governed identity tone;
- one named size;
- optional layout class.

Its named sizes encode role, not arbitrary dimensions:

| Size | Intended role |
|---|---|
| `compact` | dense secondary context |
| `row` | standard entity or fact row |
| `prominent` | emphasized list/card subject |
| `hero` | stronger summary subject |
| `detail` | detail-pane subject |
| `avatar` | identity as page subject |
| `ringed` | identity nested inside a progress ring |

The progression is meaningful: the orb can move from a small classifier beside content to the visual subject of a detail page without changing its semantic identity.

## What the orb may represent

### Entity identity

Examples:

- account type;
- transaction type;
- category;
- plan;
- goal;
- scheduled commitment;
- care identity;
- action identity.

### Fact identity

My Finance extends the model beyond records. A fact such as amount, fee, date, balance, recurrence or available cash can have a stable identity because the user repeatedly encounters the same question across forms, review rows and detail panes.

This is an important refinement:

> A fact identity names the measure or question, not the screen that happens to display it.

Thus an aggregate can still have identity. “Available” is the same measure whether shown on Home, Accounts or an inspector.

### Action identity

Actions may receive identity when they are first-class objects in a sequence, not merely generic buttons. This prevents actionable rows from visually collapsing into a grey footer beneath colorful facts.

## What the orb must not represent

### Status

Status is temporary. Identity is durable.

A transaction being overdue, pending or reconciled does not make those states its identity. Status should use explicit text, symbols, placement and accessible feedback rather than repurposing the entity’s tone.

### Navigation destination

A navigation item names a destination, not a financial object. Navigation therefore should not create a second competing identity registry.

### Decorative category color

An orb is invalid when its color is selected only to make adjacent rows varied. Variation may improve rhythm, but the registry must remain stable across contexts.

## Identity hierarchy

My Finance implies the following precedence:

```text
referenced entity identity
        outranks
fact identity
        outranks
neutral fallback
```

When a row points to a known account, plan or goal, that entity’s own identity should be shown. A generic “account” fact identity is the empty seat used before a selection exists or where no record-specific identity is available.

This supports continuity: the same object carries its identity from list row to form selection to detail pane.

## Glyph and tone responsibilities

The system deliberately separates responsibilities:

### Glyph

- survives monochrome and forced-color environments;
- carries the primary distinction;
- must not collide where facts can appear together;
- should describe the semantic object or measure.

### Tone

- reinforces identity;
- creates visual rhythm;
- helps scanning;
- must remain stable for the same identity;
- must never be the only carrier of meaning.

The strongest existing rule is effectively:

> No two facts that need to be distinguished in the same context should rely on tone alone.

## Closed registries

The architecture uses closed unions and total resolvers so missing identities become build-time problems rather than silent runtime drift.

This is especially strong for facts. An unlisted fact should not quietly become a slate orb because that hides incomplete design work. The compiler or verification suite should force an explicit decision.

## Stored color compatibility

My Finance also handles legacy or user-stored colors by mapping known color values into the governed tone vocabulary. This permits continuity with persisted data without allowing every arbitrary hex value to become a new design-system color.

Candidate principle:

> Normalize stored appearance into the semantic palette at the rendering boundary; do not expand the palette from historical data.

## Shape

The circle is not treated as a universal law yet, but it currently succeeds because it:

- is compact and visually neutral;
- behaves like identity chrome rather than a card;
- scales cleanly from row to avatar;
- nests naturally inside progress rings;
- avoids introducing another rectangular surface into dense rows;
- distinguishes identity from pills, badges and buttons.

Further cross-project validation is required before “identity must be circular” can be promoted.

## Why this is stronger than a normal icon system

A conventional design system often exposes:

- Icon;
- Avatar;
- Badge;
- color prop.

My Finance instead approaches:

- semantic identity registry;
- identity resolver;
- identity rendering primitive;
- context-specific identity adapters;
- automated verification of consumption.

The semantic registry is the innovation. The circle is its current visual expression.

## Candidate canon rules

### Candidate ID-01 — Identity precedes content

Entity rows should establish what kind of thing the user is looking at before secondary metadata.

### Candidate ID-02 — Identity is resolved, not improvised

Feature surfaces must consume governed identity rather than choosing local glyph/tone combinations.

### Candidate ID-03 — Identity is durable; status is temporary

Status, urgency and validation must not overwrite entity identity.

### Candidate ID-04 — Glyph carries meaning; tone reinforces it

Every identity must remain distinguishable without color.

### Candidate ID-05 — Referenced entities retain their own identity

When a fact points to a real entity, the entity outranks the generic fact placeholder.

### Candidate ID-06 — Measures can have identity

Repeated facts and aggregates may receive stable identity when that improves cross-surface recognition.

### Candidate ID-07 — Exceptions are classified

A surface without identity must be explicitly classified as non-entity or explain why another mechanism is superior.

## Anti-patterns

- Passing `tone="blue"` directly from arbitrary feature rows.
- Giving the same entity different icons across list, form and detail contexts.
- Using orb color as a status indicator.
- Creating navigation orbs that compete with financial identity.
- Reusing one glyph for two adjacent facts and relying on color to distinguish them.
- Adding an orb to every metric merely to satisfy a visual quota.
- Treating a decorative gradient disc as identity without a semantic registry.
- Allowing user-stored hex values to create uncontrolled tones.

## Compliance questions for new builds

1. What objects require durable identity?
2. Which identities are entities, facts, actions or roles?
3. Where is the single registry that owns glyph and tone?
4. Can any feature screen invent a local identity?
5. Does every identity remain distinct without color?
6. Does status remain separate from identity?
7. What happens when identity is missing?
8. Are legitimate orb-less surfaces explicitly classified?
9. Does identity survive list-to-detail and compact-to-wide transitions?
10. Is the chosen shape appropriate to this product profile, or merely copied from finance?

## Promotion assessment

| Criterion | Assessment |
|---|---|
| Repeated inside My Finance | Strong |
| Enforced in code | Strong |
| Solves a real usability problem | Strong |
| Accessibility rationale | Strong |
| Portable beyond finance | Probable |
| Cross-project validation | Pending |
| Ready for final canon | Not yet |

## Required next evidence

- Compare identity treatment in iVisit Console, iVisit App, WetinDey and Jelo.
- Date the first appearance of governed identity in the portfolio.
- Determine whether non-circular identity mechanisms exist and are stronger in any profile.
- Inspect forced-colors and screen-reader behavior in the rendered product.
- Verify action, fact and entity adapter coverage across My Finance.
