# My Finance Semantic Signal Color

Status: validated pattern candidate  
Source product: `Dr-dyrane/planned`  
Pass relationship: PASS-001 input to future PASS-004  
Authority: research, not final canon

## Finding

My Finance contains two distinct color systems that must not be collapsed:

1. **Identity tone** — durable color attached to what a thing is.
2. **Signal color** — temporary color attached to what needs attention, what is progressing, or what consequence is approaching.

This distinction is central to the product’s restraint. Identity color lives mainly in compact orbs. Signal color appears only where the user needs interpretation or action.

The strongest candidate rule is:

> Color must declare its job before it declares its hue.

A color token is incomplete until it is classified as identity, signal, interaction, data, or atmosphere.

## Why this matters

Many dashboard systems use color indiscriminately:

- category colors become chart colors;
- chart colors become status colors;
- status colors become button colors;
- red, yellow and green are added without defining the decision they support.

The result is visually loud but semantically weak.

My Finance is moving toward a better model:

- compact identity tones support recognition;
- signal colors describe financial condition or required attention;
- neutral surfaces carry most information;
- destructive color remains reserved;
- charts do not automatically inherit category decoration;
- state is not communicated by color alone.

## Two-layer model

### Layer 1 — Identity tone

Identity tone answers:

> What kind of thing is this?

Properties:

- durable across screens;
- resolved through a registry;
- concentrated in the Icon Orb;
- reinforced by a glyph;
- not automatically positive or negative;
- may be varied to aid scanning while remaining semantically stable.

Examples include teal for a savings account identity, coral for an expense identity, or amber for a date fact. These are not success, error or warning states.

### Layer 2 — Signal color

Signal color answers:

> What does the user need to understand or do now?

Properties:

- temporary or context-dependent;
- tied to interpretation, urgency, progress or consequence;
- must be accompanied by text, iconography, position or shape;
- should become stronger only as action need increases;
- should not overwrite the identity of the entity carrying the signal.

## Working signal ladder

The current portfolio hypothesis is a gradual ladder rather than three binary traffic-light states.

| Level | Working name | Meaning | User consequence |
|---:|---|---|---|
| 0 | Neutral | Context only; no judgment | Read if useful |
| 1 | Stable | Healthy, sufficiently funded, or on course | No action required |
| 2 | Emerging | Direction is changing but remains manageable | Awareness helpful |
| 3 | Attention | Review is warranted | Decision should be considered |
| 4 | Intervention | A meaningful correction is needed | Action should be taken |
| 5 | Critical | Immediate, irreversible, or severe consequence | User must decide now |

This is a semantic ladder. Exact hues remain provisional until implementation evidence and contrast testing are complete.

## Identity color is not emotional judgment

A coral expense orb does not mean the expense is bad. A teal savings orb does not mean the savings account is healthy. Those tones classify the object.

Health, risk and urgency require a separate signal layer.

Candidate rule:

> Never infer financial judgment from an identity tone.

This prevents a category palette from becoming an accidental moral vocabulary.

## Signal placement

Signal should be attached to the smallest surface that owns the condition.

Preferred order:

1. value or label that changed;
2. local row or card;
3. section summary;
4. page-level status;
5. modal interruption only when the decision genuinely blocks progress or protects the user.

A global red banner for a local plan issue is too loud. A tiny color dot for a critical payment failure is too weak.

Candidate rule:

> Signal strength and signal scope must match consequence strength and consequence scope.

## Progress color

Progress is directional rather than binary. A goal can be incomplete without being unhealthy.

The product’s donut and ring language suggests that progress color should communicate:

- amount completed;
- distance remaining;
- pace or timing when known;
- whether the user is still within a safe trajectory;
- transition from healthy to attention to intervention without hard decorative bands.

A smooth progression is appropriate when the underlying measure is continuous. Hard boundaries are appropriate only when the product has a real threshold, such as a deadline, minimum balance or irreversible commitment.

Candidate rule:

> Gradients may visualize continuous change; they must not invent false precision or hide real thresholds.

## Donut and ring relationship

My Finance’s strongest visual combination is the semantic identity orb nested within or paired with a progress ring:

```text
identity = what this is
ring = how it is going
copy = why it matters
```

This separation is powerful because identity remains stable while progress changes around it.

The ring must not become a decorative halo. It should encode a real measure with a textual equivalent.

## Interaction color

Interaction color is a third responsibility and should not automatically reuse identity or signal tones.

It answers:

> What can the user act on, what is selected, and where is focus?

Requirements:

- selection must remain visible without relying only on color;
- focus must be explicit and accessible;
- pressed and hover states should not change semantic meaning;
- a destructive control must not appear equivalent to a primary constructive action;
- disabled appearance must not be confused with low-priority signal.

## Neutrality as a resource

Neutrality is not absence of design. It creates contrast budget.

When most surfaces are neutral:

- identity orbs become legible without large colored cards;
- a warning can be noticed without becoming fluorescent;
- the user can compare values without category color competing for attention;
- charts and progress indicators can use color intentionally;
- dark mode does not become a field of glowing accents.

Candidate rule:

> Spend chroma where it changes recognition, interpretation or action.

## Accessibility

Color must never carry the complete message.

Every meaningful signal should include at least one additional channel:

- explicit copy;
- icon or glyph;
- shape or pattern;
- position;
- line style;
- numerical value;
- accessible status announcement.

Identity tones already follow this direction because the glyph remains when forced colors flatten the discs.

For progress indicators:

- always provide the numeric value or equivalent statement;
- ensure track and fill remain distinguishable in high contrast;
- do not depend on green-to-red discrimination;
- avoid animated color transitions as the only update feedback.

## Candidate semantic roles

The following roles should be investigated before final token names are chosen:

### Identity roles

`identity.berry`, `identity.coral`, `identity.amber`, `identity.lime`, `identity.teal`, `identity.cyan`, `identity.blue`, `identity.indigo`, `identity.violet`, `identity.slate`.

These are families, not judgments.

### Signal roles

- `signal.stable`
- `signal.emerging`
- `signal.attention`
- `signal.intervention`
- `signal.critical`
- `signal.info`
- `signal.pending`
- `signal.stale`
- `signal.conflict`

### Interaction roles

- `interaction.primary`
- `interaction.selected`
- `interaction.focus`
- `interaction.hover`
- `interaction.pressed`
- `interaction.destructive`
- `interaction.disabled`

### Data roles

- sequential scale;
- diverging scale;
- categorical series;
- comparison baseline;
- forecast/confidence region.

Data colors must be selected from chart requirements, not borrowed automatically from identity tones.

## Candidate canon rules

### Candidate CLR-01 — Color has one declared responsibility

A color use must be classified as identity, signal, interaction, data or atmosphere.

### Candidate CLR-02 — Identity does not imply judgment

Identity tone must not communicate health, urgency or success.

### Candidate CLR-03 — Signal is local-first

Place the signal near the condition it describes and escalate its scope only when the consequence is broader.

### Candidate CLR-04 — Signal strength follows consequence

Visual intensity must correspond to the urgency and reversibility of the user’s next decision.

### Candidate CLR-05 — Color reinforces; it does not stand alone

Every meaningful state remains understandable without hue.

### Candidate CLR-06 — Neutrality preserves attention

Default surfaces remain quiet so semantic color retains value.

### Candidate CLR-07 — Continuous measures deserve continuous expression

Use gradients or smooth transitions only where the underlying value is continuous; preserve explicit threshold boundaries.

### Candidate CLR-08 — Identity and progress remain separable

A changing condition may surround, annotate or accompany an identity but should not replace it.

## Anti-patterns

- Treating every green as success and every red as failure.
- Coloring a whole card because its leading orb is colored.
- Reusing category colors as chart series without checking comparison needs.
- Turning identity tones into health judgments.
- Using a red-to-green gradient without text or numeric context.
- Showing warning color globally for a local issue.
- Using low-opacity text as the only disabled-state indicator.
- Hiding a real threshold inside a decorative smooth gradient.
- Allowing stored arbitrary colors to expand the semantic palette.
- Using color to distinguish statuses that share the same label and icon.

## Compliance questions for new builds

1. What job does each color token perform?
2. Are identity, signal and interaction roles separated?
3. Can the user understand every meaningful condition without color?
4. Is the signal placed near the object that owns it?
5. Does signal intensity match consequence and reversibility?
6. Are continuous and thresholded measures represented honestly?
7. Are neutral surfaces preserving sufficient attention contrast?
8. Are charts using a data-specific palette?
9. Does dark mode preserve hierarchy without excessive glow?
10. Does a progress ring have a textual and numeric equivalent?

## Promotion assessment

| Criterion | Assessment |
|---|---|
| Clear distinction inside My Finance | Strong |
| Registry-backed identity tones | Strong |
| Signal ladder fully implemented | Partial |
| Progress/ring evidence | Strong candidate |
| Accessibility rationale | Strong |
| Cross-project validation | Pending |
| Exact token values ready | No |
| Ready for final canon | Not yet |

## Required next evidence

- Inspect actual CSS variables and contrast values for all identity tones.
- Audit donut/ring states and threshold logic.
- Compare signal treatment in iVisit emergency lifecycle and WetinDey freshness evidence.
- Determine where My Finance still conflates identity, signal and interaction color.
- Test forced colors, dark mode and color-vision-deficiency simulations.
- Define whether green/yellow/red language is appropriate globally or only for selected product profiles.
