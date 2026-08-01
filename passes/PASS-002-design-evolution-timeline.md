# PASS-002 — Design Evolution Timeline

- Status: Active
- Started: 2026-08-01
- Depends on: `PASS-001-repository-archaeology.md`
- Governing ADR: `ADR-0001-canon-as-research-and-reference-system.md`

## Purpose

Reconstruct how Dyrane UI moved from experiments and framework-shaped screens into a governed, testable interface language. This pass is chronological and causal: it must show not merely when a treatment appeared, but what defect, product pressure, or design judgment caused it to survive.

## Current thesis

The present system did not emerge as one continuous visual style. It emerged through several corrections:

1. product experimentation established breadth;
2. operational products exposed the limits of generic cards, tables and badges;
3. iVisit Console made borderless composition, semantic hue and shared mobile grammar explicit;
4. My Finance separated visual roles into governed semantic registries and made design decisions executable;
5. the Dyrane UI Canon now extracts those decisions into a product-independent reference system.

## Provisional generations

### Generation 0 — Learning and framework inheritance

Approximate evidence pool: ALX repositories, clones, exercises and early React experiments.

Characteristics:

- framework or assignment structure dominates;
- limited authored product grammar;
- components are implementation units rather than semantic contracts;
- visual decisions cannot safely establish canon.

These repositories remain historical context, not design authority.

### Generation 1 — Product and brand experiments

Evidence pool: Wave, Get, Doit, Kiosks, Bill, Flash, Rockspot, Portfolio and related early products.

Questions for continued audit:

- first use of strong brand color;
- first recurring card anatomy;
- first attempts at mobile navigation;
- first use of animation as product character;
- first signs of low-border or borderless composition.

No current claim from this generation is promoted without source inspection.

### Generation 2 — Domain products and richer information architecture

Evidence pool: SaySwitchBank, Kleva Kit, Reflectify, SmartEdu, Slatechain, H2O, MedChart and related systems.

Likely shifts:

- products gain persistent navigation and multi-screen information architecture;
- domain semantics begin to shape components;
- dashboards and record management become recurring page types;
- status color, badges and cards become common, sometimes excessively.

This generation is expected to contain both ancestors and anti-canon evidence.

### Generation 3 — Operational density and spatial products

Evidence pool: iVisit, iVisit App and early iVisit Console.

Pressures introduced:

- emergency state;
- maps and location;
- providers, patients and organizations;
- dense operational tables;
- mobile and desktop parity;
- permissions and irreversible commands;
- live data and asynchronous truth.

This pressure made decorative consistency insufficient. The interface needed state ownership, command honesty and repeatable page grammar.

### Generation 4 — The July 2026 iVisit Console pivot

Strong dated evidence: July 6–10, 2026.

The console's own commit history records an explicit migration away from:

- premium glass as default surface treatment;
- red brand color as universal emphasis;
- shadcn Card/Table/Badge chrome;
- borders and hairlines as default separation;
- one-off mobile page structures;
- decorative gradients, glows and excessive shadows;
- source-only confidence in visual correctness.

It moved toward:

- borderless CSS-grid and transparent-row composition;
- canonical squircle radii;
- literal semantic hues for success, warning and information;
- per-hue active states instead of global brand-red selection;
- shared mobile list anatomy;
- adaptive grouping based on the actual data distribution;
- truthful loading: skeleton on first assembly, quiet updating on refetch;
- fail-closed commands where receiver authority is absent;
- live computed-style verification in addition to source gates;
- design-system harnesses that guard structural grammar.

This is the first currently verified moment where “canon” became an explicit implementation concern across an estate rather than a preference applied screen by screen.

#### Important correction

Borderless UI should not be documented as a timeless Dyrane trait. The evidence currently supports a stronger and more honest statement:

> Borderless composition became a deliberate Dyrane doctrine when operational products demonstrated that generic card, table and badge chrome obscured hierarchy and fragmented the estate.

### Generation 5 — My Finance semantic governance

Strong dated evidence: July 30–31, 2026.

My Finance takes the iVisit lesson—shared grammar and enforced restraint—and moves it from visual cleanup into semantic architecture.

Verified developments include:

- finance surfaces must lead entities with governed identity orbs or record a justified exception;
- the gate asserts semantics rather than freezing markup;
- identity, fact, action, status and navigation are treated as separate roles;
- status cannot borrow identity color as its only carrier;
- forced-colors behavior is considered in glyph assignment;
- facts receive unique glyphs and stable identities across ask/review/detail surfaces;
- actions eventually receive registry-owned identities after in-context visual review showed plain glyphs read as a dead footer;
- archived object identity is preserved across data boundaries, not just inside render components;
- contradictory gates are corrected rather than treated as authority;
- page and surface grammar become executable architecture.

This is the first currently verified stage where Dyrane UI becomes a semantic system capable of explaining why two visually similar leading marks must be different primitives.

### Generation 6 — Canon extraction and product-independent reference

Current repository: `dyrane-ui-canon`.

Goals:

- distinguish portfolio history from build authority;
- promote only evidence-backed rules;
- define project profiles so new builds inherit logic without visual cloning;
- publish machine-readable contracts;
- preserve provenance, contradictions and supersession.

## First-seen chronology table

| Concept | First explicit evidence currently verified | Maturity point | Confidence |
|---|---|---|---|
| Estate-wide borderless doctrine | iVisit Console, 2026-07-07 | Multiple page clusters rebuilt and hard-gated | High |
| Semantic hue over brand-red emphasis | iVisit Console, 2026-07-07 to 2026-07-10 | Per-hue active KPI chips and literal status palettes | High |
| Shared mobile page grammar | iVisit Console, 2026-07-08 to 2026-07-10 | LIST donor, adaptive grouping, dock/FAB checks | High |
| Truthful loading distinction | iVisit Console, 2026-07-09 | Skeleton for assembly; updating state for warm refetch | High |
| Static-gate versus rendered-style distinction | iVisit Console, 2026-07-10 | Opacity compiler defect and computed-style rule | High |
| Governed entity identity orb | My Finance, established before 2026-07-30; hard-gated 2026-07-30 | Registry, adapters and surface grammar gate | High |
| Identity/fact/action/status/navigation role separation | My Finance, 2026-07-31 | PlainGlyph, FactOrb, ActionOrb and registry corrections | High |
| Tests pin semantics rather than chrome | My Finance, 2026-07-30 | Accessible grouping, target and pressed-state gates | High |
| Design choices as architectural tests | iVisit Console then My Finance | My Finance broad architecture suite | High |

## Causal chain

```text
Generic framework surfaces
        ↓
Operational inconsistency and excessive chrome
        ↓
iVisit Console borderless and semantic-color pivot
        ↓
Shared grammar plus enforcement harnesses
        ↓
My Finance semantic registries and role ownership
        ↓
Dyrane UI Canon as reusable reference system
```

## Findings promoted only to hypothesis

1. iVisit Console is likely the bridge between visual taste and explicit estate-wide doctrine.
2. My Finance is likely the bridge between doctrine and semantic/executable architecture.
3. The finest current Dyrane pattern is not “an orb plus color”; it is role ownership:
   - object identity owns an identity primitive;
   - facts own stable measure/question identities;
   - actions own an action registry;
   - status uses state grammar;
   - navigation uses destination grammar.
4. Borderlessness is a means of reducing false grouping, not a prohibition on every divider.
5. Semantic color matured from status mapping into role-aware local meaning.

## Required continuation

- audit pre-2026 products to identify ancestors rather than assume none existed;
- inspect iVisit App chronology separately from Console;
- establish whether identity islands or avatar discs preceded My Finance Icon Orb;
- compare Jelo and commerce products where imagery may outrank glyph identity;
- inspect AU Mosaic and Sanctum for atmosphere, composition and motion ancestry;
- add commit-level evidence references for every timeline claim;
- distinguish founder decisions from agent-generated language where possible.

## Exit criteria

PASS-002 completes when:

- at least 15 products have dated design milestones;
- every major candidate law has a plausible origin and maturation point;
- false “always true” narratives are removed;
- contradictions and superseded doctrines are explicitly recorded;
- the timeline can guide a new project without requiring historical imitation.
