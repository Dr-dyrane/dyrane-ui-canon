# Dyrane UI Canon

> A borderless, spatial, evidence-aware interface system that compresses complexity into calm, progressively disclosed structures.

The Dyrane UI Canon is the design constitution for products created by Dyrane. It is not a mood board, a collection of preferred Tailwind classes, or an imitation of Apple interfaces. It is an evidence-backed system derived from the repeated decisions, successful patterns, failures, and architectural evolution across the Dr-dyrane GitHub portfolio.

## Canon status

**Phase:** Research foundation  
**Reference implementation:** `Dr-dyrane/planned` (My Finance)  
**Primary comparative systems:** iVisit Console, iVisit App, WetinDey, Jelo, AU Mosaic, Sanctum World Workspace, Capsule, Hop, Equal, EngineerOS  
**Target audit:** approximately 50 repositories, with 15–20 receiving deep code-level review

The canon is provisional until a rule survives cross-project comparison. My Finance is the current reference implementation because it converts design intent into reusable primitives, page grammars, validation scripts, accessibility contracts, and architecture tests. Other products may remain category leaders: iVisit for operational urgency, WetinDey for map-first interaction, Jelo for consumer warmth, and Sanctum for immersive workspace behavior.

## What belongs here

A canon rule must describe more than appearance. It should define:

1. **Intent** — the human or product problem being solved.
2. **Observable behavior** — what people see, feel, or can do.
3. **Structural contract** — the component, layout, state, or navigation requirement.
4. **Evidence** — projects and files where the pattern appears.
5. **Confidence** — proposed, emerging, established, or constitutional.
6. **Exceptions** — where the rule should not apply.
7. **Failure mode** — the predictable result of violating it.
8. **Verification** — how design review, tests, or linting can enforce it.

## Core working thesis

Dyrane UI moves complexity away from the visible surface and into structure. The interface should feel calm not because the product is simple, but because hierarchy, context, state, and action are resolved before decoration.

The emerging language is characterized by:

- borderless tonal hierarchy;
- strong spatial composition and clear scroll ownership;
- progressive disclosure instead of permanent density;
- semantic rather than decorative color;
- mobile layouts that transform rather than merely shrink;
- contextual intelligence placed beside decisions;
- motion that explains topology and state;
- terse copy with recoverable detail;
- explicit loading, empty, partial, ready, and error states;
- reusable page grammars and surface contracts;
- forgiving interaction with visible consequences and reversibility.

## Repository map

```text
canon/              Normative design rules
methodology/         Research, evidence, scoring, and copyright policy
research/            Repository inventory, audits, comparisons, and timeline
decisions/           Architectural decision records
specifications/      Machine-readable tokens and implementation contracts
examples/            Canonical page and interaction grammars
```

## Authority levels

| Level | Meaning |
|---|---|
| Constitutional | Required across Dyrane products unless an ADR records an exception |
| Established | Repeated successfully across multiple mature products |
| Emerging | Strong in one mature product or recurring in several incomplete products |
| Proposed | Candidate rule awaiting comparative evidence |
| Deprecated | Previously used but now considered harmful or obsolete |

## Initial constitutional candidates

These are hypotheses, not yet final rulings:

1. Structure before decoration.
2. Tonal separation before borders.
3. One dominant action per state.
4. Progressive disclosure before persistent density.
5. Motion must preserve spatial causality.
6. Color must carry semantic responsibility.
7. Mobile is a distinct spatial composition.
8. Intelligence appears as guidance, not as detached chatbot furniture.
9. Feedback belongs near the object or action it describes.
10. Every consequential action needs a legible result, recovery path, or explicit irreversible boundary.

## Research sequence

1. Inventory eligible repositories.
2. Separate original product work from tutorials, clones, backend-only repositories, and abandoned scaffolds.
3. Perform broad structural review across approximately 50 repositories.
4. Conduct deep audits of the strongest 15–20 systems.
5. Score projects using a consistent rubric.
6. Extract repeated patterns, contradictions, and regressions.
7. Compare gaps against current platform guidance and established accessibility standards.
8. Promote surviving rules into the canon.
9. Derive component contracts, tokens, and automated verification.

## Source policy

Apple Human Interface Guidelines and other external standards are references, not text to be copied into this repository. Their principles are paraphrased, adapted, and attributed. Limited quotations may be used only where legally appropriate and necessary for analysis. The Dyrane canon must remain an original system grounded in Dyrane products.

## Current documents

- [Research method](methodology/research-method.md)
- [Scoring framework](methodology/scoring-framework.md)
- [Apple HIG adaptation policy](methodology/apple-hig-adaptation.md)
- [My Finance reference audit](research/projects/planned.md)

## Maintainer

Alexander Udeogaranya / Dr-dyrane
