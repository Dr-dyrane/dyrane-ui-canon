# Project Scoring Framework

## Purpose

The scorecard compares interface-system maturity, not beauty in isolation. A product can be visually impressive and still score poorly if its hierarchy is fragile, state behavior is incomplete, mobile adaptation is superficial, or patterns cannot be reused.

Each deep-audit project receives a score out of 100. Scores are evidence-backed and provisional until representative journeys and implementation files have been inspected.

## Weighted dimensions

| Dimension | Weight |
|---|---:|
| Structural coherence | 18 |
| Information hierarchy | 12 |
| Interaction grammar | 12 |
| State and feedback completeness | 12 |
| Responsive transformation | 10 |
| Reusable system architecture | 10 |
| Visual restraint and craft | 8 |
| Accessibility and alternate input | 8 |
| Motion coherence | 5 |
| Product intelligence and trust | 5 |
| **Total** | **100** |

## Rating scale

Each dimension is scored from 0–5, then multiplied by its weight.

| Score | Interpretation |
|---|---|
| 0 | Absent, broken, or impossible to assess |
| 1 | Ad hoc; major failures dominate |
| 2 | Partially functional but inconsistent or shallow |
| 3 | Competent and mostly coherent |
| 4 | Strong, deliberate, and reusable |
| 5 | Reference-level; explicit, enforced, and resilient |

Weighted score formula:

```text
project score = sum((dimension rating / 5) × dimension weight)
```

## 1. Structural coherence — 18%

Measures whether the interface has a stable spatial and architectural grammar.

Inspect:

- canonical page types;
- shell and navigation consistency;
- scroll ownership;
- content regions and containment;
- master-detail behavior;
- modal, sheet, and pane hierarchy;
- route-to-layout correspondence;
- separation between structure and feature styling.

### Reference-level evidence

- page grammars are named or inferable;
- common surfaces use shared primitives;
- navigation depth remains legible;
- transient layers do not compete for ownership;
- layout contracts are tested or documented;
- mobile and desktop preserve conceptual continuity.

### Common deductions

- arbitrary card grids without a page grammar;
- nested scrolling with unclear ownership;
- sidebars, sheets, and modals used interchangeably;
- duplicated layout code that drifts across routes;
- visual grouping dependent entirely on borders.

## 2. Information hierarchy — 12%

Measures whether people can immediately identify context, priority, state, and next action.

Inspect:

- title and context hierarchy;
- primary versus secondary actions;
- density and grouping;
- typography roles;
- metadata placement;
- progressive disclosure;
- visual competition;
- empty and partial information states.

### Reference-level evidence

- every screen has a clear reading order;
- the dominant action matches the current state;
- supporting detail is available without being permanently loud;
- visual emphasis follows product importance rather than component availability.

## 3. Interaction grammar — 12%

Measures consistency and predictability across controls, gestures, navigation, forms, and direct manipulation.

Inspect:

- control semantics;
- tap, click, keyboard, pointer, and gesture behavior;
- selection versus navigation distinction;
- disclosure patterns;
- form composition;
- destructive action handling;
- cancellation and escape;
- direct-manipulation continuity.

### Reference-level evidence

- similar actions behave similarly;
- gestures have visible alternatives;
- controls react immediately;
- cancellation is possible before commitment;
- interaction does not depend on hidden novelty;
- repeated tasks avoid unnecessary ceremony.

## 4. State and feedback completeness — 12%

Measures how clearly the product communicates availability, progress, results, failure, and recovery.

Required states where relevant:

- loading;
- empty;
- partial or stale;
- ready;
- pending mutation;
- success;
- recoverable error;
- terminal error;
- offline or degraded;
- permission denied;
- destructive confirmation;
- undo or recovery.

### Reference-level evidence

- feedback appears near the affected object;
- interruption matches consequence;
- success is confirmed only when meaningful;
- errors explain what failed and what can happen next;
- pending state prevents ambiguous duplicate actions;
- color is never the only signal;
- global toasts supplement rather than replace local truth.

## 5. Responsive transformation — 10%

Measures whether the product intentionally recomposes across viewport, orientation, input, and device class.

Inspect:

- region priority changes;
- list-detail transformation;
- toolbar and navigation adaptation;
- touch target preservation;
- sheet and pane behavior;
- text scaling;
- safe areas and browser chrome;
- orientation and standalone PWA behavior.

### Reference-level evidence

- mobile is not a compressed desktop;
- conceptual context survives reflow;
- important actions remain reachable;
- density changes deliberately;
- controls match the likely input method;
- layout avoids breakpoint-only thinking where container behavior is more appropriate.

## 6. Reusable system architecture — 10%

Measures whether design intent is encoded into reusable, enforceable implementation structures.

Inspect:

- tokens;
- primitives;
- component contracts;
- variant discipline;
- shared state patterns;
- page templates;
- test coverage;
- linting or verification scripts;
- ADRs and documentation.

### Reference-level evidence

- rules survive new feature work;
- repeated components share anatomy and behavior;
- semantic tokens outnumber raw decorative values;
- verification catches visual or interaction drift;
- exceptions are explicit rather than accidental.

## 7. Visual restraint and craft — 8%

Measures quality, precision, and emotional appropriateness—not decoration quantity.

Inspect:

- spacing rhythm;
- typography;
- color temperature;
- radius logic;
- icon consistency;
- surface hierarchy;
- shadows and materials;
- chart treatment;
- dark and light modes;
- visual noise.

### Reference-level evidence

- every visual treatment has a role;
- whitespace creates hierarchy;
- border use is exceptional and intentional;
- color remains semantically accountable;
- decorative atmosphere does not weaken legibility;
- details feel authored at both macro and micro scales.

## 8. Accessibility and alternate input — 8%

Measures whether the product remains usable across ability, preference, environment, and input method.

Inspect:

- semantic structure;
- labels and names;
- focus order and visibility;
- keyboard access;
- target size and spacing;
- contrast;
- text scaling and reflow;
- reduced motion;
- non-color signals;
- gesture alternatives;
- screen-reader state announcements;
- error association.

### Reference-level evidence

- accessibility is built into primitives;
- custom controls preserve semantic equivalence;
- critical information has redundant modalities;
- focus follows visual and task order;
- motion reduction preserves meaning;
- automated checks are supplemented by manual review.

## 9. Motion coherence — 5%

Measures whether animation clarifies state, hierarchy, causality, and spatial continuity.

Inspect:

- origin and destination continuity;
- gesture tracking;
- duration and easing;
- interruptibility;
- frequency of repeated animation;
- loading and progress motion;
- reduced-motion equivalents;
- large-area movement;
- animation performance.

### Reference-level evidence

- motion answers where an object came from or went;
- direction matches the interaction;
- feedback animation is brief;
- frequent controls are not burdened by decorative delay;
- transitions can be interrupted;
- reduced motion substitutes opacity, state change, or instant topology without losing information.

## 10. Product intelligence and trust — 5%

Measures how recommendations, automation, AI, prediction, and sensitive product logic preserve agency and evidence.

Inspect:

- placement of guidance;
- confidence and evidence;
- explanation of automated decisions;
- reversibility;
- consent and permission context;
- data provenance;
- distinction between suggestion and action;
- failure behavior.

### Reference-level evidence

- intelligence appears in the task context;
- the system does not impersonate certainty;
- consequential automation requires clear boundaries;
- people can inspect, reject, correct, or reverse recommendations;
- AI does not become a detached parallel navigation system.

## Score confidence

Every final project score includes a confidence marker:

- **Low:** manifest or shallow code scan only;
- **Medium:** representative files and multiple journeys inspected;
- **High:** broad code, state, responsive, and historical evidence inspected;
- **Verified:** implementation plus running-product or screenshot validation and contradiction review.

## Provisional benchmark

My Finance is the provisional reference product, not an automatic perfect score. It leads because design intent is increasingly enforced through page contracts, architecture tests, progressive-disclosure checks, accessibility verification, state models, and reusable surface primitives. Its final score remains open until the full audit identifies inconsistencies, regressions, and missing experiential evidence.
