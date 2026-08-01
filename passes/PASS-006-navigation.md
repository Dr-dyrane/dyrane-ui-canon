# PASS-006 — Navigation and Spatial Truth

Status: Active
Confidence: Medium-high for map-first products

## Objective

Define navigation as preservation and transformation of context, not merely route changes.

## Current model

The iVisit map system separates five layers:

1. **Truth layer** — the persistent map and live journey.
2. **Viewport** — what portion of truth is currently visible.
3. **Persistent shell** — the sheet, modal, panel, or sidebar containing the task.
4. **Phase** — the current decision or state within the shell.
5. **Detail** — deeper information, comparison, forms, or transient overlays.

## Findings

### 1. Phase changes do not imply place changes

`MapPhaseTransitionView` changes content inside a persistent shell while the map remains mounted. The motion is intentionally small because the user is still in the same spatial system.

Candidate rule:

> Navigation strength should match contextual displacement.

### 2. Responsive transformation may change the navigation model

A bottom sheet can become a sidebar or panel. In sidebar presentation, sheet detents and drag interactions are disabled rather than awkwardly preserved.

Candidate rule:

> Preserve task and state across viewports; do not preserve an interaction model that no longer fits.

### 3. Phase payload preserves return context

Decision and commitment phases carry source phase, source snap state, hospital, location, and related payload. This allows returning to the correct spatial and decision context instead of resetting to a generic root.

Candidate rule:

> Navigation state includes provenance, not only destination.

### 4. Persistent consequences should live above transient phases

The tracking audit showed that rating UI failed when rendered inside the tracking phase because phase exit unmounted it. The later architecture lifted rating state and rendering above transient phase ownership.

Candidate rule:

> A consequence that must survive navigation belongs to the nearest persistent owner above that navigation layer.

### 5. Viewport ownership must be singular

The map, sheet, phase, and tracking layers should not independently issue contradictory camera or padding commands. A future camera audit must identify one owner for fit, center, and obstruction in each phase.

Candidate rule:

> One viewport has one active camera authority at a time.

## Required specification

Each navigation transition should declare:

- origin layer
- destination layer
- persistent context
- discarded context
- back/close consequence
- focus destination
- viewport consequence
- motion class
- recovery state

## Gaps

- Current camera authority and padding ownership remain under source audit.
- Browser/back-button behavior is not yet mapped.
- Deep-link entry into commitment and tracking phases is not yet verified.
- Cross-product validation against My Finance master-detail and WetinDey map flow remains pending.
