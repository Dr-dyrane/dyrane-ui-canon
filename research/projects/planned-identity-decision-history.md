# My Finance — Identity Decision History

- Repository: `Dr-dyrane/planned`
- Audit depth: D4 reference audit
- Scope: Icon Orb, semantic role ownership, forced-colors resilience, gate design
- Status: Evidence-backed research; not yet final canon

## Why this document exists

The current Icon Orb system can look inevitable when read only in its finished form. The commit history shows the opposite: its strongest rules were discovered through concrete failures, reversals and visual arbitration.

That history matters for the canon. A reusable rule should preserve the problem solved, not fossilize the current markup.

## Decision sequence

### 1. Surface grammar becomes enforceable

Commit: `a704c7b8e618eafc0fb4e3debc437fc7cac41329` — 2026-07-30

The project records that visual grammar had survived as tribal knowledge while behavior and contract tests remained green. The founder still had to catch visual drift by eye.

The new gate established:

- component-authored sheet bodies own their padding;
- entity surfaces lead with Icon Orb;
- exceptions must be classified with a written reason;
- Care shares the primitive instead of inventing a parallel chip.

### Canon implication

A design rule becomes mature when the system can distinguish a violation from a justified exception. “Use Icon Orb everywhere” would have been weaker than the implemented rule.

---

### 2. Gates stop pinning transient chrome

Commit: `64c7f10bc04f7a6ab38391b869022d7b36bd9d68` — 2026-07-30

A transaction-type step changed visual form three times. Markup-sensitive checks failed each time even though the product semantics remained valid.

The replacement checks asserted:

- accessible grouping;
- use of an accepted row primitive;
- a minimum target large enough for touch;
- exposed selected state through `aria-pressed`.

### Canon implication

> Compliance gates should pin the invariant, not the current costume.

This is a foundational rule for the future Dyrane compliance system.

---

### 3. Reconciliation exposes identity versus status

Commit: `67d7d32cc903b80aaa3a6c25028374a165eedf83` — 2026-07-31

A duplicate marker used an amber `Repeat2` orb for every row. This failed for two reasons:

1. `Repeat2` already had a stable registry meaning elsewhere;
2. “possible duplicate” is a temporary status, not the identity of a transaction.

The corrected row used the transaction’s own resolved identity. Direction was also restored textually and numerically because the orb and sign were decorative to assistive technology.

### Canon implication

- An entity retains its identity while passing through states.
- Status may annotate identity but must not replace it.
- Direction and consequence cannot rely on hidden visual decoration.

---

### 4. Initial overcorrection: actions have no orb

Commit: `c962c6277ef12388f0264e5d3195804885ee0273` — 2026-07-31

The first role-separation correction interpreted actions and destinations as things without identity. It introduced `PlainGlyph` for leading slots that did not identify a financial object.

This solved real problems:

- one AlertTriangle glyph no longer relied on five colors to distinguish five situations;
- page destinations no longer invented a second tone registry;
- plans and goals received distinct glyphs after tone was removed;
- archived entity identity was preserved through the data boundary;
- settings and pane headers converged on one leading-slot primitive.

### Valid part of the decision

Navigation and status should not use finance identity tones merely to fill the leading slot.

### Part later reversed

The conclusion that actions have no identity proved too broad.

---

### 5. Visual arbitration reverses the action rule

Commit: `36b116c3821cac25961f2ce30c11a3f7e23ab015` — 2026-07-31

In context, action rows followed a column of colored entity and fact orbs with plain gray glyphs. The result looked like a dead footer rather than the usable part of the page.

The project reversed course:

- actions receive identity;
- action identity comes from a closed registry;
- call sites provide an action key, not a local icon or tone;
- no two destructive or adjacent actions may depend on color alone;
- status and navigation remain excluded.

This is an especially important Dyrane lesson: semantic rigor is not achieved by making every role visually austere. A role can have identity without pretending to be an entity.

### Canon implication

The mature role model is:

| Role | Primitive | Ownership |
|---|---|---|
| Entity | Identity orb/avatar/image | Entity/category registry |
| Fact or measure | Fact orb | Fact registry |
| Action | Action orb | Action registry |
| Status | Status copy, pill, vital track or signal | State model |
| Navigation | Plain/destination glyph | Navigation model |

---

## The distinctive contribution

The most valuable My Finance design is not the circular shape or the ten-color palette in isolation.

It is this rule:

> A leading visual mark must declare which semantic role it represents, and its glyph and tone must be owned by that role’s registry rather than improvised by the screen.

That enables:

- consistency across pages;
- meaningful forced-colors behavior;
- stable identity across responsive transformations;
- reliable archived and hydrated states;
- agent-readable implementation contracts;
- exceptions that can be reasoned about rather than hidden.

## Accessibility reasoning

The system explicitly assumes tone can disappear:

- forced-colors mode can flatten tone families;
- monochrome printing can remove hue;
- users may not distinguish hue reliably.

Therefore:

- glyphs must remain distinguishable;
- adjacent facts and actions should not share a glyph when confusion is consequential;
- text and accessible names carry direction, state and outcome;
- color reinforces meaning rather than serving as the only channel.

## Risks for canonization

1. **Registry inflation** — not every label deserves its own permanent glyph.
2. **Visual noise** — a page of equally weighted orbs can destroy hierarchy.
3. **False universality** — commerce may use product imagery; people may use avatars; maps may use pins.
4. **Role ambiguity** — an action can target an entity and may need both action and entity context.
5. **Circular-shape overfitting** — the semantic architecture is more important than the circle.
6. **Local contrast** — ten tones require verified contrast across light, dark and forced-color modes.

## Promotion candidates

### Candidate ID-01

Identity is resolved before rendering.

### Candidate ID-02

Glyph carries the primary non-text distinction; tone reinforces it.

### Candidate ID-03

Status never replaces object identity.

### Candidate ID-04

Navigation does not borrow domain identity color without a domain reason.

### Candidate ID-05

Actions may have identity, but action identity belongs to an action registry.

### Candidate ID-06

Compliance checks pin semantic invariants, not one markup arrangement.

### Candidate ID-07

Semantic identity must survive data transformation, archiving and responsive presentation boundaries.

## Next evidence required

- inspect actual CSS tone values and contrast;
- audit all Icon Orb consumers by role;
- count exceptions and determine whether they remain justified;
- inspect progress-ring and hero compositions;
- compare iVisit identity islands and status discs;
- compare Jelo product imagery and human avatars;
- test whether the architecture survives a non-finance project profile.
