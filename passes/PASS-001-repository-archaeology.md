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

- [x] at least 50 owned repositories have been classified;
- [x] all primary UI-bearing candidates have an audit-depth assignment;
- [ ] at least 15 high-value products have structured audits;
- [ ] My Finance has a complete reference audit;
- [ ] a provisional portfolio ranking exists;
- [ ] an evolution timeline identifies major shifts in Dyrane UI;
- [ ] recurring principles and contradictions are documented;
- [x] the next specialized passes have clear evidence-backed scopes.

## Repository classes

### Class A — Reference candidate

Mature products with strong authored UI, reusable structure, meaningful states, and enough evidence for deep inspection.

### Class B — Comparative product

Meaningful product UI capable of validating, contradicting, or dating a candidate principle.

### Class C — Evolutionary evidence

Smaller or older products useful for tracing design development and first appearances.

### Class D — Excluded from primary visual scoring

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

### Batch 1 — Reference triangulation

- My Finance / `planned`
- iVisit Console
- iVisit App
- WetinDey
- Jelo
- AU Mosaic
- Sanctum World Workspace
- Capsule

### Batch 2 — Product-family validation

- Hop
- Equal
- EngineerOS
- H2O by Dyrane
- Slatechain
- SmartEdu Frontend
- SaySwitchBank
- Kleva Kit
- Scholarix
- Reflectify

### Batch 3 — Historical and focused evidence

Remaining Class B and C repositories in `research/repository-inventory.md`.

## Dedicated research tracks opened by this pass

### Identity Language

Key question: Is Icon Orb a local finance pattern or a general Dyrane identity primitive?

Current research document: `research/my-finance-identity-architecture.md`.

Evidence collected from My Finance:

- closed identity tone vocabulary;
- entity, transaction, schedule and fact resolvers;
- named role-based orb sizes;
- explicit separation of identity from status and navigation;
- glyph-first accessibility rationale;
- entity-over-fact precedence;
- build-time pressure against missing fact identities;
- classified exceptions enforced by verification scripts.

Next evidence:

- identity treatment in iVisit Console, iVisit App, WetinDey and Jelo;
- non-circular identity mechanisms;
- first-seen chronology;
- rendered accessibility behavior.

### Signal Color

Key question: Does Dyrane UI use color primarily as semantic signal rather than decoration or category branding?

Current research document: `research/my-finance-semantic-signal-color.md`.

Evidence collected from My Finance:

- identity tones are durable classification, not judgment;
- status must remain separate from identity;
- progress rings can surround stable identity without replacing it;
- neutral surfaces preserve chroma for recognition and attention;
- forced-colors rationale requires non-color distinctions;
- continuous progress and true thresholds require different expression.

Next evidence:

- actual tone variables and contrast values;
- donut/ring threshold logic;
- iVisit urgency signals;
- WetinDey evidence freshness;
- dark mode and forced-colors validation.

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
- The Identity Orb is not merely a component; it is the rendering end of a semantic identity pipeline.
- My Finance separates durable identity tone from temporary signal state in principle, though full signal implementation still requires audit.
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
- Identity tone variation can support scanning but may become decorative if registry rationale is weak.
- A general Dyrane identity law may require multiple approved renderers rather than one mandatory circular orb.

Contradictions are evidence. They should produce profiles or scoped rules, not be erased.

## Work log

### 2026-08-01 — Foundation

- Established methodology and scoring framework.
- Began My Finance reference audit.
- Accepted ADR-0001.
- Added continuity and pass control documents.

### 2026-08-01 — Inventory and identity batch

- Normalized a 50-repository primary candidate set.
- Separated coursework, backend-only, empty and unresolved low-evidence repositories.
- Defined three audit waves and provisional audit depth.
- Extracted the My Finance Identity Architecture.
- Extracted the My Finance Semantic Signal Color model.
- Promoted Identity and Signal from informal observations to validated-pattern candidates; neither is final canon yet.

## Quantitative progress

- Owned repositories discovered: more than 70
- Primary candidate inventory: 50 / 50 classified
- Class A reference candidates: 16
- Deep audits completed: 0 final; My Finance remains in progress
- Structured/deep audits required for pass exit: 15
- Specialized research tracks with source documents: 2
- Final canon rules promoted: 0

## Next actions

1. Create PASS-002 for the design evolution timeline.
2. Inspect chronology and representative files for the first eight Wave 1 repositories.
3. Deepen My Finance around actual tone CSS, progress rings, state thresholds, motion and feedback.
4. Begin structured audits for iVisit Console and iVisit App.
5. Build the provisional project scorecard.
6. Update `STATUS.md` after the next comparison batch.

## Exit output

PASS-001 should end with:

- a complete inventory;
- project scorecard;
- evolution timeline;
- first canon promotion candidates;
- recommended specialized passes;
- explicit carry-forward context.
