# PASS-004 — Interaction

Status: Active
Confidence: Medium-high for iVisit map sheet interactions

## Objective

Define how Dyrane interfaces assign interaction ownership, distinguish observation from commitment, and recover safely from interruption or failed authority.

## Findings

### 1. One gesture path should own one behavior

The map shell separates handle/header/body gesture regions, disables sheet gestures in sidebar presentation, and uses a dedicated Android expanded-body collapse path. This reduces responder competition.

Candidate rule:

> Every gesture has one semantic owner, one activation contract, and one recovery path.

### 2. Interaction thresholds should encode consequence

Half-to-collapsed requires stronger pull or velocity than expanded-to-half. This is appropriate because collapsing removes more visible context.

Candidate rule:

> The more context an interaction removes, the stronger the demonstrated intent should be.

### 3. Scroll and posture must not fight

The detent system does not snap mid-scroll. It records drag evidence and commits on release. It also requires edge conditions and meaningful travel before changing posture.

Candidate rule:

> Content exploration owns ordinary scroll; container posture changes only at explicit boundaries.

### 4. Tracking actions are policy-derived

`useMapTrackingController` builds action-surface policy and derives primary, secondary, destructive, middle, and bottom actions from lifecycle state rather than rendering every possible command.

Candidate rule:

> Action availability is a product-state decision, not a presentation convenience.

### 5. Foreground work owns a busy state

Tracking wraps consequential asynchronous actions in a named `busyAction`, clears it in `finally`, and surfaces success or failure feedback. This is preferable to a global spinner because the busy state remains attached to the initiating action.

Candidate rule:

> Pending feedback remains local to the action that caused it unless the whole surface is genuinely blocked.

### 6. Fallbacks preserve intent

ETA sharing attempts the system share sheet, then falls back to clipboard, and reports the actual outcome. User intent survives platform capability differences.

Candidate rule:

> When a platform cannot perform the preferred action, preserve the user’s intent through the nearest honest fallback.

## Interaction classes

- Observe
- Explore
- Select
- Compare
- Commit
- Monitor
- Recover
- End

Each class should define:

- trigger
- immediate feedback
- pending behavior
- cancellation
- success consequence
- failure recovery
- accessibility equivalent

## Gaps

- Explicit keyboard actions for sheet posture outside phase-local controls.
- A shared destructive-action confirmation standard.
- Formal optimistic-update rules.
- Cross-project validation against finance actions and console bulk actions.
