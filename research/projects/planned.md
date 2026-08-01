# My Finance (`Dr-dyrane/planned`)

## Audit status

**Classification:** Class A — canon-defining  
**Role:** Provisional reference implementation  
**Audit confidence:** Medium  
**Current phase:** Architecture and enforcement review; running-product and full journey review still pending

## Why it is the provisional benchmark

My Finance is currently the strongest candidate for reference status because design intent is not confined to screenshots, comments, or shared components. The repository contains explicit verification scripts that encode page grammar, surface identity, attention layers, master-detail defaults, responsive behavior, progressive disclosure, typography, accessibility, mutation integrity, and other interface contracts.

This does not make it automatically perfect. It makes it unusually inspectable and resistant to drift.

A crucial distinction is visible in the repository’s own surface-grammar gate: the rules are described as having been derived from accepted shipped surfaces, including named exceptions, rather than invented as abstract conventions. This is close to the research method required for the wider Dyrane canon.

## Evidence reviewed

### Manifest and test architecture

`package.json` exposes a broad architecture suite covering, among other areas:

- page contracts;
- viewport sovereignty;
- surface grammar;
- typography-weight contracts;
- finance-surface contracts;
- progressive disclosure;
- master-detail and layers;
- accessibility and focus;
- form identity;
- modal behavior;
- shared canvas atmosphere;
- offline and sync behavior;
- money-display consistency;
- guidance and advisor boundaries.

This is stronger evidence than dependency choice alone because the design system has executable failure conditions.

### Surface grammar gate

Source: `scripts/verify-surface-grammar.mjs`

Observed contracts:

1. **Sheet bodies own their content padding.** `StandardSheet` owns header and footer padding, while body composition remains explicit. This prevents accidental flush content and clarifies primitive responsibility.
2. **Entity rows lead with an identity orb.** Accepted account, movement, goal, plan, schedule, and reconciliation surfaces share a governed identity pattern.
3. **Exceptions are classified with reasons.** Metric and synthesis surfaces may omit the orb because they represent measures or page-level answers rather than entities.
4. **Care shares the same visual grammar.** A closed care-identity registry chooses meaning; call sites do not choose arbitrary glyphs or tones.
5. **Semantic registries precede visual primitives.** Product meaning resolves to a governed key before rendering through the shared orb component.

Canon implications:

- repeated entities require stable visual identity;
- semantic meaning should select appearance, not feature call sites;
- exceptions belong in explicit classifications;
- primitives should own a narrow responsibility rather than silently padding every region;
- a component that cannot be classified may indicate a missing page or entity grammar.

### Master-detail and attention-layer gate

Source: `scripts/verify-master-detail-and-layers.mjs`

Observed contracts:

1. **Attention layers are named semantically.** Chrome, passive status, notifications, popovers, modal backdrops, modals, detail surfaces, critical decisions, and authentication-critical surfaces use role tokens rather than arbitrary z-index values.
2. **Attention order is enforced.** Passive status yields to popovers, notifications, and modals.
3. **Passive state cannot compete with modal ownership.** Sync status is suppressed or visually yields when an aria-modal dialog owns attention.
4. **Input capability affects form treatment.** Coarse-pointer contexts enforce a 16 px form-control floor, including landscape cases.
5. **Every major wide layout has a meaningful default inspector.** Home, Plan, Accounts, Activity, and Settings do not leave the detail column empty.
6. **Array order does not invent selection.** The first account, transaction, or goal is not automatically treated as the user’s chosen object.
7. **The persistent inspector remains structurally present.** Selection state changes its content, not the existence of the column.
8. **Compact and wide presentations diverge intentionally.** Advisor content routes to the persistent detail pane on wide layouts and to a sheet on compact layouts.
9. **Full-canvas composition is protected.** Major pages reject arbitrary centered maximum widths.
10. **Container behavior governs workspace columns.** Accounts and Activity respond to their available container rather than relying only on viewport breakpoints.
11. **Sync conflict is not reduced to a generic global toast.** Conflict resolution is routed to the profile/settings context where consequence can be explained.

Canon implications:

- z-index is a product-attention system, not a local styling number;
- wide empty space should carry meaningful context rather than collapse unpredictably;
- default context is safer than inferred entity selection;
- responsive transformation should change presentation while preserving conceptual function;
- global transient feedback must not replace contextual conflict resolution;
- canvas width follows product grammar, not a universal centered-column habit.

## Emerging My Finance principles

### MF-01 — Design rules must be executable where possible

**Status:** Emerging  
**Evidence:** E1 implementation, E3 enforcement

A mature Dyrane system should convert repeated visual and interaction decisions into verification. Human review remains necessary, but obvious drift should fail automatically.

Candidate verification forms:

- AST or source checks for forbidden primitives;
- component tests for interaction state;
- token validation;
- accessibility tests;
- route and page-contract checks;
- screenshot or visual-regression tests where stable enough.

### MF-02 — Identity precedes decoration

**Status:** Emerging

An entity chooses a semantic identity key. A governed registry maps that key to symbol, tone, and treatment. Feature surfaces do not improvise icons or category color.

Failure mode:

- arbitrary icon/color selection causes the same entity type to look unrelated across surfaces;
- visual category systems grow without semantic control;
- product teams encode business logic in presentation details.

### MF-03 — Attention is a finite ordered resource

**Status:** Emerging

Every transient layer participates in a global attention hierarchy. A passive status cannot visually compete with a critical decision, and a toast cannot sit above a modal merely because a component library chose a large z-index.

Proposed attention order:

```text
canvas
< chrome
< passive status
< popover
< notification
< modal backdrop
< modal
< elevated modal
< persistent or focused detail
< critical decision
< authentication-critical boundary
```

The exact ordering remains subject to cross-project comparison.

### MF-04 — Permanent regions require meaningful defaults

**Status:** Emerging

A persistent desktop inspector should begin with page or section context, not emptiness and not an arbitrarily selected first entity.

This protects user agency and uses wide-screen space productively.

### MF-05 — Responsive design preserves function while changing presentation

**Status:** Emerging

The same conceptual object may appear as a permanent pane on wide screens and a sheet or route on compact screens. The implementation may differ, but the role, state, and identity remain coherent.

### MF-06 — Conflict resolution belongs at the consequence boundary

**Status:** Emerging

A sync conflict involving replacement of local data is not ordinary status. It belongs in a context that can explain the competing copies, consequence, and decision.

### MF-07 — Exceptions must be named

**Status:** Emerging

A system becomes more trustworthy when legitimate exceptions are enumerated with reasons instead of silently excluded from enforcement.

## Provisional score

This score reflects architecture evidence only and will change after visual, responsive, and journey validation.

| Dimension | Rating | Weighted result | Notes |
|---|---:|---:|---|
| Structural coherence | 4.7/5 | 16.9/18 | Explicit page, master-detail, layer, and canvas contracts |
| Information hierarchy | 4.1/5 | 9.8/12 | Strong contextual defaults; full visual review pending |
| Interaction grammar | 4.0/5 | 9.6/12 | Broad contract evidence; gesture and live-product validation pending |
| State and feedback completeness | 4.4/5 | 10.6/12 | Sync, mutation, offline, conflict, and guidance tests are extensive |
| Responsive transformation | 4.5/5 | 9.0/10 | Permanent-pane and compact-sheet adaptation plus container rules |
| Reusable system architecture | 4.9/5 | 9.8/10 | Current category leader |
| Visual restraint and craft | 3.9/5 | 6.2/8 | Requires systematic visual review |
| Accessibility and alternate input | 4.1/5 | 6.6/8 | Strong verification signals; manual assistive-tech review pending |
| Motion coherence | 3.4/5 | 3.4/5 | Some motion-specific tests exist; full grammar not yet assessed |
| Product intelligence and trust | 4.3/5 | 4.3/5 | Advisor boundaries, evidence, conflict honesty, and guidance architecture |
| **Provisional total** |  | **86.2/100** | Medium confidence |

## Strengths

- design intent is converted into executable contracts;
- exceptions are reasoned rather than hidden;
- responsive behavior is structural, not merely breakpoint styling;
- attention layers use semantic roles;
- entity identity is governed;
- persistent detail is treated as a page grammar;
- conflict and offline behavior acknowledge product truth;
- the codebase recognizes interface drift as an architectural failure.

## Risks and unanswered questions

1. **Verification may become regex-bound.** Source-pattern gates can protect conventions but may also reward textual compliance without guaranteeing experiential quality.
2. **The system may overfit its current implementation.** Rules derived from one codebase need cross-product testing before becoming constitutional.
3. **Identity orbs may become universal furniture.** The exception system is promising, but wider review must ensure orbs remain semantically useful rather than mandatory decoration.
4. **Persistent detail can become compulsory density.** Wide layouts need validation to ensure the inspector adds decision value rather than filling space.
5. **Visual and motion quality remain under-evidenced.** Code contracts cannot fully establish rhythm, comfort, timing, or perceived continuity.
6. **Platform behavior needs live testing.** PWA standalone mode, mobile browser chrome, keyboard, screen reader, and reduced-motion paths require experiential validation.

## Reference status decision

My Finance remains the provisional reference implementation because it currently demonstrates the most complete bridge between product philosophy, reusable interface architecture, and automated enforcement.

Reference status means:

- start comparative analysis here;
- reuse its strongest proven contracts;
- identify where other products outperform it;
- do not universalize finance-specific presentation;
- do not treat current code as beyond criticism;
- require cross-project evidence before constitutional promotion.

## Next audit actions

- inspect `docs/design-system.md` and `docs/dyrane-page-contract.md`;
- map the canonical page grammars in `lib/page-grammar.ts`;
- inspect shared tokens and global surface atmosphere;
- trace Home, Plan, Accounts, Activity, and Settings journeys;
- inspect motion and reduced-motion implementation;
- inspect all local mutation feedback patterns;
- compare mobile navigation and sheet behavior against iVisit and WetinDey;
- test the provisional score against at least five other Class A products.
