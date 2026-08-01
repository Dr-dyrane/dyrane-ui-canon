# New-Build Reference System

## Purpose

This document defines how a new Dyrane product consumes the canon.

A new product should not need to inspect historical repository audits, unresolved hypotheses, or external comparison notes. It should receive a compact, authoritative design contract assembled from promoted laws, decisions, canon rules, patterns, specifications, tokens, and a product profile.

## Required inputs

Before implementation begins, record:

- product name;
- product domain;
- primary users;
- primary user outcome;
- dominant objects;
- highest-risk action;
- irreversible actions;
- expected information density;
- primary device classes;
- offline requirements;
- real-time requirements;
- whether AI or automation is present;
- accessibility constraints beyond the baseline;
- brand constraints;
- known reference products.

## Select a product profile

A profile expresses one valid family of Dyrane UI. Initial planned profiles include:

- finance workspace;
- healthcare emergency;
- map-first community;
- operational console;
- consumer commerce;
- editorial marketing;
- immersive workspace;
- personal utility;
- data-heavy administration.

Profiles can vary in density, imagery, navigation, motion intensity, and dominant surface while remaining canon-compliant.

## Declare the dominant page grammar

Every major route must declare one primary grammar:

- Dashboard
- List
- Hybrid
- Master-detail
- Workspace
- Map-first
- Guided decision flow
- Operational console
- Editorial catalogue

A page may compose secondary grammars, but one must own its top-level topology.

## Define identity

For each dominant object, define:

- object class;
- visible name;
- identity primitive;
- icon, image, avatar, marker, or orb ownership;
- semantic tone ownership;
- fallback identity;
- accessibility label;
- selected state;
- disabled state;
- compact representation;
- wide representation.

The Icon Orb is preferred for governed symbolic entities, but it is not universally mandatory. Photography, avatars, map markers, documents, or branded marks may lead where they communicate identity more truthfully.

## Define semantic signals

Create a signal table before choosing hues.

Each signal must specify:

- semantic meaning;
- trigger condition;
- urgency;
- scope;
- expected user action;
- whether color is necessary;
- secondary non-color cue;
- entry and exit behavior;
- persistence;
- accessibility name.

Do not assign colors to categories merely to make the interface lively.

## Define state completeness

Every significant surface must account for:

- initial loading;
- empty;
- partial;
- ready;
- stale;
- offline;
- optimistic;
- saving;
- success;
- recoverable error;
- blocking error;
- permission denied;
- conflict;
- destructive confirmation;
- terminal completion.

Not every state must be visible at once, but each must have an intentional presentation.

## Define feedback ownership

Use the smallest sufficient feedback level:

1. inherent control feedback;
2. local passive status;
3. local action result;
4. transient cross-context confirmation;
5. interruptive warning;
6. terminal or irreversible boundary.

A toast is not the default response to every mutation. A modal is not the default response to every error.

## Define motion responsibility

Every animation must explain at least one of:

- topology;
- causality;
- state;
- focus;
- continuity.

Record:

- trigger;
- property animated;
- duration or spring behavior;
- interruption behavior;
- reduced-motion equivalent;
- input modality considerations;
- whether repeated use makes the animation burdensome.

## Define responsive topology

For every major route, describe:

- compact layout;
- regular layout;
- wide layout;
- what becomes a sheet;
- what becomes a route;
- what remains persistent;
- scroll ownership;
- focus restoration;
- object and task continuity.

Responsive behavior is a change in presentation topology, not a smaller desktop screenshot.

## Define intelligence and automation

Where AI or automation exists, define:

- source facts;
- inferred facts;
- confidence representation;
- user-review boundary;
- reversible actions;
- irreversible actions;
- evidence access;
- pending work;
- failure behavior;
- privacy boundary;
- audit history.

AI must not impersonate certainty or silently commit consequential actions.

## Required output

Every new product should create:

```text
DESIGN-CONTRACT.md
```

The contract should include:

1. Product thesis
2. Selected profile
3. Governing laws and ADRs
4. Page grammar map
5. Object identity registry
6. Semantic signal table
7. Surface and layer map
8. Responsive topology
9. State matrix
10. Feedback matrix
11. Motion contract
12. Accessibility requirements
13. AI and automation contract
14. Approved deviations
15. Compliance plan

## Compliance levels

### Core compliant

The product follows the constitutional and accessibility requirements, communicates state honestly, uses semantic identity and signal color responsibly, and provides intentional responsive topology.

### System compliant

The product additionally uses canonical page grammars, surface rules, interaction patterns, specifications, and tokens.

### Reference implementation

The product additionally contains automated verification or tests that prevent meaningful design drift.

## Deviations

A deviation is acceptable when:

- the product domain creates a genuine need;
- the governing rule is identified;
- the reason is documented;
- accessibility and trust are preserved;
- the deviation is scoped;
- a review trigger is defined.

A deviation should create a project ADR. It does not automatically change the central canon.

## Feedback loop

New builds may discover patterns the canon lacks.

Such discoveries return to research mode as evidence. They must pass through validation and promotion before becoming central rules. This keeps the canon alive without allowing every implementation choice to rewrite it.
