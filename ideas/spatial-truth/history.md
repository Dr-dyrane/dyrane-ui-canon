# Spatial Truth — History

Status: research hypothesis
Primary origin candidate: `Dr-dyrane/ivisit-app`

## Definition

Spatial truth is the practice of keeping the user's real or operational world stable while interface layers change around it.

In iVisit App, the map remains the persistent representation of location, nearby care, route, and responder movement. The bottom sheet changes question, density, and commitment level without pretending that each step is a new world.

## Earliest strong evidence

### January 8, 2026

`EmergencyBottomSheet.jsx` became the primary emergency surface through a sequence of improvement commits. Tracking was added for ambulance routes, ETA, and bed-booking status.

### January 9, 2026

Search focus began coordinating sheet expansion and header suppression. This demonstrated that spatial truth requires chrome coordination, not merely a map background.

### April 21, 2026

The map-and-sheet specification explicitly defined:

- map as reality;
- sheet as state and decision;
- route shell as persistent;
- detail as expansion before replacement;
- auth and payment as late commitments.

## Why it matters

Traditional multi-step interfaces often discard context between screens. In emergency care, that can hide:

- where the request begins;
- which provider is selected;
- where help is moving;
- whether the user is still exploring or has committed.

A persistent spatial layer lowers reorientation cost and makes state changes feel causal.

## Candidate rule

> Preserve the most important truth layer while secondary interface layers change around it.

The truth layer may be:

- a map in emergency and discovery products;
- a ledger or plan context in finance;
- a document or canvas in a workspace;
- a patient timeline in clinical software.

The canon should not require maps. It should require identifying and preserving the product's dominant truth layer.

## Related candidate principles

- one dominant decision per state;
- progressive commitment;
- chrome yields to task;
- motion preserves topology;
- interface state does not outrun authoritative state.

## Risks

- persistence can become clutter if every control remains visible;
- sheets can become miniature route stacks;
- map-first layouts can reduce accessibility if essential content exists only spatially;
- gesture-only detents can exclude keyboard and assistive-technology users;
- preserving context must not prevent a focused full-screen commitment step when consequence requires one.

## Promotion gate

Promote only after validation in at least two non-map products and one additional map-first product.