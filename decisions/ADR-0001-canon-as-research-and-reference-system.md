# ADR-0001 — Canon as Research and Reference System

- Status: Accepted
- Date: 2026-08-01
- Decision owners: Dr Dyrane Alexander and maintainers of the Dyrane UI Canon
- Supersedes: None
- Superseded by: None

## Context

The Dyrane UI Canon is being extracted from a large portfolio of products, experiments, consoles, mobile applications, commercial builds, and platform work. The repository must preserve the historical and comparative research that reveals the system, but it must also become an authoritative reference for future products.

A research archive alone would be too slow and ambiguous for implementation. A style guide alone would hide the evidence, reasoning, contradictions, and evolution that make the system trustworthy. The repository therefore needs two linked operating modes:

1. **Research mode** discovers, compares, scores, challenges, and validates design principles.
2. **Reference mode** exposes only promoted, implementation-ready guidance to new products, engineers, designers, and AI agents.

The repository must also remain resumable after context loss. A maintainer should be able to read a small set of control documents and know the current pass, completed work, unresolved questions, next action, and governing decisions.

## Decision

The Dyrane UI Canon will operate as both:

- an evidence-backed research system; and
- an executable reference system for new products.

The two modes will remain structurally separate but traceable.

### Research mode contains

- repository audits;
- screenshots and code evidence;
- comparative studies;
- scoring records;
- hypotheses;
- contradictions;
- rejected interpretations;
- external references;
- active passes.

Research material may be incomplete or contradictory. It is not automatically authoritative.

### Reference mode contains

- laws;
- accepted ADRs;
- canon rules;
- page and interaction patterns;
- specifications;
- tokens;
- project profiles;
- starter briefs;
- compliance checks;
- reference implementations.

Only promoted material in reference mode may govern a new build.

## Authority order

When two documents conflict, the following order applies:

1. `laws/`
2. accepted `decisions/`
3. `canon/`
4. `patterns/`
5. `specifications/`
6. `tokens/`
7. `profiles/`
8. project-specific design contracts
9. implementation examples
10. research notes

Higher authority wins. A lower layer may specialize a higher layer but may not silently contradict it.

## Promotion pipeline

No observation enters the canon directly. The normal path is:

```text
Evidence
  → Research observation
  → Hypothesis
  → Cross-project validation
  → Decision or law candidate
  → Canon rule
  → Pattern or specification
  → Token or implementation contract
  → Compliance check
```

A rule may skip a stage only when the reason is documented.

## New-build reference workflow

Every new Dyrane product should be able to consume the canon without reading the full research archive.

The expected workflow is:

1. Select or create a product profile.
2. Declare the dominant objects, user goals, risk boundaries, and page grammars.
3. Select the identity system and semantic signal model.
4. Define compact and wide topology.
5. Define state, feedback, motion, and interruption contracts.
6. Generate a project-specific `DESIGN-CONTRACT.md`.
7. Implement against canon specifications and tokens.
8. Run a compliance review.
9. Record justified deviations as project ADRs.
10. Feed genuinely new evidence back into the canon research system.

A project may express Dyrane UI differently without becoming visually identical to My Finance. The canon governs principles, semantics, topology, interaction, and quality—not one fixed skin.

## Continuity protocol

The repository will always maintain:

- `STATUS.md` — the authoritative current state;
- one active pass document under `passes/`;
- accepted decisions under `decisions/`;
- a repository inventory and scoring ledger;
- explicit next actions.

When a maintainer says **continue**, the default meaning is:

1. Read `STATUS.md`.
2. Read the active pass.
3. Verify the most recent completed item.
4. Execute the next listed action.
5. Update the relevant research or reference documents.
6. Update the active pass and `STATUS.md`.
7. Commit the work and report the SHA.

## Consequences

### Positive

- Research can remain exploratory without contaminating implementation guidance.
- New projects receive a compact and authoritative reference package.
- Design decisions remain traceable to evidence.
- Context loss does not require rediscovery.
- AI agents can consume structured rules rather than infer taste from screenshots.
- The canon can evolve without rewriting history.
- My Finance can remain the top reference implementation without forcing every product to resemble a finance app.

### Costs

- More documentation discipline is required.
- Findings must be promoted deliberately.
- Status and pass files must be updated with every meaningful batch.
- Some discoveries will remain provisional longer than they would in an informal style guide.
- Contradictions must be recorded rather than smoothed over.

## Compliance

This ADR is satisfied when:

- research and reference material are stored separately;
- `STATUS.md` identifies one active pass and one next action;
- every canonical rule contains evidence or an accepted rationale;
- every new-build profile points to the governing canon and specifications;
- project-specific deviations are explicit;
- a new maintainer can resume by reading the continuity documents only.

## Reconsideration triggers

Revisit this decision only if:

- the repository becomes too difficult to consume for new builds;
- the promotion pipeline blocks useful implementation work;
- machine-readable specifications require a different authority model;
- multiple product families demonstrate that one canon cannot govern them coherently.
