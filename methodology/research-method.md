# Research Method

## Purpose

This repository reconstructs Dyrane UI from evidence across the Dr-dyrane portfolio. The method is designed to prevent three common errors:

1. mistaking recent preference for enduring principle;
2. mistaking framework defaults for authored design language;
3. mistaking visual polish for product-system maturity.

The canon must be descriptive before it becomes normative. It first records what repeatedly exists, then evaluates whether the pattern is useful, and only then promotes it into a rule.

## Unit of analysis

A repository is not treated as a single design artifact. Each eligible project is examined through several layers:

- product purpose and user pressure;
- information architecture;
- page and navigation grammar;
- layout topology and scroll ownership;
- surface hierarchy;
- component anatomy;
- interaction and gesture behavior;
- feedback and state communication;
- motion and transition logic;
- responsive transformation;
- accessibility and alternate input;
- design tokens and visual language;
- implementation architecture;
- tests, verification scripts, and documented decisions;
- regressions, abandoned patterns, and contradictions.

## Eligibility classes

### Class A — canon-defining

Mature original products with meaningful interface breadth, active architecture, and enough implementation evidence to support rules. These receive deep audits.

Expected examples include My Finance, iVisit Console, iVisit App, WetinDey, Jelo, AU Mosaic, Sanctum World Workspace, Capsule, Hop, Equal, EngineerOS, Scholarix, H2O by Dyrane, Slatechain, SmartEdu, and SaySwitchBank.

### Class B — evolutionary evidence

Original products or experiments that reveal recurring instincts, transitional patterns, or useful failures but may lack maturity or breadth. These receive focused audits.

### Class C — contextual evidence

Small prototypes, portfolio work, landing pages, or incomplete products. These may support a narrow claim but cannot establish a constitutional rule alone.

### Class D — excluded from visual scoring

Coursework, tutorial reproductions, clones, algorithm repositories, backend-only systems, generated scaffolds, and repositories without authored interface decisions. They may still provide architectural chronology but do not count toward design-frequency claims.

## Evidence types

Each finding is tagged by evidence strength.

| Evidence | Meaning |
|---|---|
| E1 — implementation | A concrete component, layout, token, route, interaction, or test exists in code |
| E2 — repeated implementation | The same design logic appears independently in multiple products |
| E3 — enforcement | Tests, linting, contracts, ADRs, or reusable primitives protect the pattern |
| E4 — outcome | The pattern resolves a documented usability, consistency, accessibility, or maintenance problem |
| E5 — explicit intent | Product notes, commit history, issues, or documentation state the rationale |
| E6 — external alignment | The pattern aligns with current platform or accessibility guidance |

A constitutional rule should normally have E2 plus at least one of E3, E4, or E5. External alignment alone cannot make a rule Dyrane canon.

## Confidence model

### Proposed

A plausible rule supported by one project or a limited sample. It remains open to contradiction.

### Emerging

A recurring pattern supported by multiple projects, or strongly enforced in one mature reference product.

### Established

A repeated successful pattern found across different product categories and supported by implementation evidence.

### Constitutional

A rule considered foundational across Dyrane products. It has strong cross-project evidence, a clear human rationale, implementation guidance, known exceptions, and a verification path.

### Deprecated

A pattern previously used but now rejected because it causes hierarchy, usability, accessibility, maintenance, or product-trust problems.

## Audit sequence

### Pass 1 — inventory

For each repository record:

- product category;
- current status;
- UI technology;
- primary surfaces;
- probable originality;
- interface breadth;
- screenshot or preview availability;
- candidate deep-audit priority.

### Pass 2 — structural scan

Inspect manifests, route structure, shared components, layout primitives, token files, global styles, navigation, state components, and verification scripts. This pass identifies where authored design decisions live.

### Pass 3 — representative journeys

Trace at least three journeys where available:

1. first-use or entry;
2. core repeated task;
3. consequential or error-prone task.

The goal is to observe continuity across state, feedback, interruption, recovery, and responsive behavior—not merely isolated screens.

### Pass 4 — visual and interaction audit

Evaluate hierarchy, density, surfaces, typography, color, interaction, feedback, motion, accessibility, and platform fit using the scoring framework.

### Pass 5 — extraction

Record candidate rules in this format:

```yaml
rule: Feedback belongs near the object it describes
status: emerging
intent: Preserve context and reduce interpretation cost
evidence:
  - project: planned
    location: pending
    type: E1
  - project: ivisit-console
    location: pending
    type: E2
exceptions:
  - Global service outages may require a page-level message
failure_mode: Detached toast-only feedback makes result ownership ambiguous
verification: Mutation surfaces expose local pending, success, and failure states
```

### Pass 6 — contradiction testing

Before promotion, search for mature projects where the proposed rule is absent or intentionally reversed. Determine whether the contradiction is:

- a product-specific exception;
- an older design stage;
- a regression;
- a framework constraint;
- evidence that the proposed rule is too broad.

### Pass 7 — canon promotion

Promoted rules are written as original Dyrane guidance and include:

- principle;
- rationale;
- required behavior;
- preferred implementation;
- responsive and accessibility implications;
- exceptions;
- anti-patterns;
- evidence;
- verification checklist.

## External standards

External guidance is used to fill gaps and test robustness, not to overwrite portfolio evidence. Sources should be current, authoritative, and primary where possible.

Primary external references may include:

- Apple Human Interface Guidelines;
- WCAG and WAI-ARIA specifications;
- platform documentation for iOS, macOS, Android, and the web;
- established browser and framework specifications.

When external guidance supplies a missing rule, the repository must label it as **adopted**, not **extracted**. The wording must be original and the source must be linked.

## Research integrity

- Do not infer a complete interaction from a component name alone.
- Do not treat generated or copied code as authored evidence without corroboration.
- Do not award maturity merely for a large dependency list.
- Do not confuse animation quantity with motion quality.
- Do not score inaccessible novelty as craft.
- Do not hide contradictions to preserve a preferred narrative.
- Do not promote a rule without recording its failure mode.
- Do not copy copyrighted design guidance as a substitute for analysis.

## Deliverables

The research phase should produce:

- an inventory of approximately 50 eligible repositories;
- a scored comparison table;
- deep audits of 15–20 products;
- an evolution timeline;
- a catalogue of recurring patterns and anti-patterns;
- a source-backed gap analysis;
- the normative Dyrane UI Canon;
- machine-readable design tokens;
- implementation and review checklists;
- candidate automated verification rules.
