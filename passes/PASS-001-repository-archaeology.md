# PASS-001 — Repository Archaeology

- Status: Active
- Started: 2026-08-01
- Owner: Dr Dyrane Alexander
- Working agent: ChatGPT
- Governing decision: `decisions/ADR-0001-canon-as-research-and-reference-system.md`

## Purpose

Survey the Dyrane GitHub portfolio deeply enough to distinguish durable design principles from isolated styling, framework defaults, generated code, tutorial inheritance, and product-specific constraints.

This pass creates the evidence base from which laws, canon rules, specifications, profiles, and new-build contracts can later be promoted.

## Completion criteria

PASS-001 is complete when all of the following are true:

- at least 50 owned repositories have been classified;
- all meaningful UI-bearing repositories have an audit depth assignment;
- at least 15 high-value products have structured audits;
- My Finance has a complete reference audit;
- a provisional portfolio ranking exists;
- an evolution timeline identifies major shifts in Dyrane UI;
- recurring principles and contradictions are documented;
- the next specialized passes have clear evidence-backed scopes.

## Repository classes

### Class A — Canon-defining

Mature products with strong authored UI, reusable structure, meaningful states, and enough evidence for deep inspection.

### Class B — Evolutionary

Products that reveal important transitions, experiments, or partial versions of later Dyrane ideas.

### Class C — Supporting

Limited UI products, small experiments, landing pages, or specialized builds that may validate a narrow principle.

### Class D — Excluded from visual scoring

Coursework, algorithm exercises, backend-only repositories, empty repositories, clones, or products whose visible design is predominantly inherited.

Class D repositories may still provide architectural evidence but cannot establish visual canon.

## Audit depth

- **D0 — Inventory only:** name, purpose, stack, eligibility.
- **D1 — Surface scan:** README, package metadata, major routes, global styles.
- **D2 — Structured audit:** navigation, page grammar, identity, color, states, responsiveness.
- **D3 — Deep audit:** implementation primitives, interaction contracts, motion, accessibility, screenshots, tests, and architecture.
- **D4 — Reference audit:** exhaustive enough to support canon promotion and comparison.

My Finance is assigned D4.

## Scoring dimensions

Use `methodology/scoring-framework.md`.

Each scored project must include:

- raw dimension scores;
- evidence confidence;
- strengths;
- weaknesses;
- distinct contributions;
- likely inherited conventions;
- canon candidates;
- anti-canon evidence;
- comparison projects.

## Evidence protocol

Every nontrivial claim should identify one or more of:

- repository and file path;
- commit or branch;
- route or component;
- screenshot or deployed surface;
- test or verification script;
- repeated pattern across multiple files;
- explicit design documentation.

Observations must distinguish:

- what exists;
- what it appears to mean;
- how confident the interpretation is;
- whether it is unique, recurring, or contradicted.

## Current batches

### Batch 1 — Reference baseline

- My Finance / `planned`
- iVisit Console
- iVisit App
- WetinDey
- Jelo

### Batch 2 — Mature composition and workspace systems

- AU Mosaic
- Sanctum World Workspace
- Capsule
- Hop
- Equal

### Batch 3 — Product breadth

- EngineerOS
- Scholarix
- Enugu Drip
- H2O by Dyrane
- Slatechain
- SmartEdu Frontend
- SaySwitchBank
- Kleva Kit
- Reflectify
- DrDyrane

### Batch 4 — Evolutionary and supporting evidence

At least 30 additional UI-bearing repositories selected from the normalized inventory.

## Dedicated research tracks opened by this pass

### Identity Language

Key question: Is Icon Orb a local finance pattern or a general Dyrane identity primitive?

Evidence to collect:

- semantic registries;
- glyph ownership;
- tone ownership;
- size and density variants;
- selection and focus behavior;
- repeated entity-row anatomy;
- non-orb identity mechanisms;
- accessibility naming;
- cases where an orb harms clarity.

### Signal Color

Key question: Does Dyrane UI use color primarily as semantic signal rather than decoration or category branding?

Evidence to collect:

- color registries;
- state tables;
- gradients;
- progress transitions;
- warning and intervention behavior;
- selection color;
- dark-mode adaptation;
- color-only failures;
- project-specific brand palettes.

### Page Grammar

Key question: Which page structures recur regardless of domain?

Candidate grammars:

- dashboard;
- list;
- hybrid;
- master-detail;
- workspace;
- map-first;
- guided decision flow;
- operational console;
- editorial catalogue.

### Motion and Feedback

Key question: Which motion and feedback behaviors are authored Dyrane conventions, and which need to be imported or strengthened from external guidance?

### Product Intelligence

Key question: How should AI, recommendations, evidence, confidence, automation, and reversibility appear within a Dyrane product?

## Current findings

Provisional only:

- My Finance is the strongest current reference because it converts design choices into enforced architecture.
- Identity orbs appear to be one of the most distinctive authored primitives.
- Borderless hierarchy is recurring, but must be validated across older and non-finance products.
- Dyrane responsive behavior increasingly changes topology rather than merely width.
- The strongest work uses semantic color sparingly and locally.
- The portfolio appears to move from styled screens toward governed interface grammars.

## Open contradictions

- Some earlier products may rely heavily on borders, card grids, or decorative gradients.
- Brand-heavy products may require stronger decorative color than My Finance allows.
- Operational consoles may legitimately prioritize density over calm spaciousness.
- Map-first products may use identity markers differently from list-first products.
- Consumer commerce may need imagery to lead identity rather than Icon Orb.

Contradictions are evidence. They should produce profiles or scoped rules, not be erased.

## Work log

### 2026-08-01

- Established methodology and scoring framework.
- Began My Finance reference audit.
- Accepted ADR-0001.
- Added continuity and pass control documents.

## Next actions

1. Create `research/repository-inventory.md`.
2. Normalize approximately 50 eligible repositories.
3. Mark audit depth and batch for each.
4. Deepen My Finance Identity Orb and signal-color evidence.
5. Update `STATUS.md` after the batch.

## Exit output

PASS-001 should end with:

- a complete inventory;
- project scorecard;
- evolution timeline;
- first canon promotion candidates;
- recommended specialized passes;
- explicit carry-forward context.
