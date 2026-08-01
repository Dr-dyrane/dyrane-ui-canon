# Apple HIG Adaptation Policy

## Purpose

Dyrane products frequently aim for the clarity, continuity, restraint, and tactile confidence associated with well-designed Apple software. This document defines how Apple Human Interface Guidelines influence the canon without turning Dyrane UI into imitation or reproducing copyrighted guidance.

## Copyright and authorship rule

The repository does **not** copy Apple Human Interface Guidelines wholesale or verbatim. Apple guidance is summarized, paraphrased, attributed, and transformed into original Dyrane rules. Short quotations may appear only when necessary for analysis and must remain limited.

The objective is to understand the underlying human-factors principle, test it against Dyrane products, and encode it in implementation language appropriate to web, PWA, React Native, and cross-platform systems.

## Classification of Apple-derived material

Every externally informed canon rule must use one of these labels:

- **Aligned** — Dyrane independently demonstrates the same principle.
- **Adapted** — Apple guidance fills a gap and is rewritten for Dyrane products.
- **Platform-specific** — useful only when targeting an Apple platform.
- **Rejected** — inappropriate for Dyrane’s product, platform, brand, or user context.
- **Unresolved** — needs implementation or usability evidence.

## Current official source set

Primary references:

- Apple Human Interface Guidelines — design principles  
  https://developer.apple.com/design/human-interface-guidelines/design-principles
- Apple Human Interface Guidelines — motion  
  https://developer.apple.com/design/human-interface-guidelines/motion
- Apple Human Interface Guidelines — feedback  
  https://developer.apple.com/design/human-interface-guidelines/feedback
- Apple Human Interface Guidelines — gestures  
  https://developer.apple.com/design/human-interface-guidelines/gestures
- Apple Human Interface Guidelines — accessibility  
  https://developer.apple.com/design/human-interface-guidelines/accessibility

Source review date: 2026-08-01.

## Adapted foundation principles

Apple’s current foundation emphasizes purpose, familiarity, flexibility, simplicity, craft, delight, responsibility, consistency, context preservation, and clear feedback. Dyrane UI adopts the human intent but expresses it through product-system rules.

### 1. Purpose becomes task sovereignty

**Dyrane rule:** Every surface must reveal what the person is here to understand or accomplish. Decorative hierarchy may not compete with task hierarchy.

Implementation consequences:

- one dominant purpose per page state;
- secondary actions are visually and spatially subordinate;
- empty states point toward meaningful first action;
- metrics without a decision or interpretation role are removed or demoted;
- AI suggestions appear only where they alter a real decision.

### 2. Familiarity becomes predictable grammar

**Dyrane rule:** A person should learn a behavior once and reuse that understanding everywhere.

Implementation consequences:

- identical affordances retain identical consequences;
- selection, navigation, disclosure, and mutation remain visually distinct;
- familiar gestures are not reassigned to surprising product-specific actions;
- custom controls preserve platform semantics and keyboard behavior;
- similar entities share detail, edit, archive, and delete grammar.

### 3. Flexibility becomes context-preserving adaptation

**Dyrane rule:** Responsive design may change composition, but it must preserve identity, task position, and causal continuity.

Implementation consequences:

- desktop master-detail may become mobile push navigation or a full-height sheet;
- the selected entity remains legible through transformation;
- navigation does not reset merely because the viewport changes;
- pointer, keyboard, touch, assistive technology, and reduced-motion behavior are designed together;
- mobile prioritizes reachability and sequence instead of shrinking desktop chrome.

### 4. Simplicity becomes resolved complexity

**Dyrane rule:** Simplicity is the result of structural resolution, not feature removal or hidden ambiguity.

Implementation consequences:

- disclose detail progressively;
- keep high-frequency actions close and immediate;
- reveal advanced options only when relevant;
- replace explanatory paragraphs with clear structure, labels, and state;
- never hide a consequential boundary merely to make a surface appear clean.

### 5. Craft becomes systemic precision

**Dyrane rule:** Quality must remain consistent across edge states, not only hero screens.

Implementation consequences:

- loading, empty, partial, offline, error, and destructive states receive authored treatment;
- spacing and typography follow semantic roles;
- motion, focus, hit targets, and copy are reviewed as craft;
- reusable primitives carry accessibility and behavior by default;
- a polished screenshot cannot compensate for incoherent interaction.

### 6. Delight becomes humane fluency

**Dyrane rule:** Delight should arise from ease, confidence, continuity, and subtle recognition—not spectacle.

Implementation consequences:

- use restrained microfeedback for meaningful completion;
- preserve user work and provide recovery;
- avoid forced tours and ceremonial transitions;
- keep repeated actions fast;
- reserve expressive animation for moments with emotional or explanatory value.

### 7. Responsibility becomes visible system honesty

**Dyrane rule:** The interface must distinguish what is known, inferred, pending, automated, reversible, and irreversible.

Implementation consequences:

- confidence and evidence accompany recommendations where material;
- permissions explain purpose before the system prompt when context is needed;
- automation exposes scope and consequence;
- failure does not masquerade as empty data;
- destructive actions state what will be removed and whether recovery exists;
- financial, medical, safety, and location interfaces avoid false certainty.

## Motion adaptation

Apple’s guidance treats motion as a tool for status, feedback, instruction, and continuity, while warning against gratuitous movement, nonoptional communication, disorienting direction, excessive duration, and uninterruptible sequences. Dyrane UI adopts these principles as a stricter motion grammar.

### Constitutional motion rules

#### Motion must explain one of five things

A motion is permitted only when it communicates at least one of:

1. **Topology** — where a view or object comes from and where it goes.
2. **Causality** — which action produced which result.
3. **State** — what changed, is pending, succeeded, or failed.
4. **Focus** — what now requires attention.
5. **Continuity** — which object remains the same across representations.

If animation communicates none of these, remove it.

#### Direction must preserve spatial causality

- A surface revealed from an edge should return toward the same edge unless the navigation model explicitly changes.
- A selected item expanding into detail should maintain a perceptual relationship to its origin.
- Back navigation should reverse or resolve the forward transition rather than introduce a new unrelated direction.
- Dragged surfaces follow the pointer or finger during direct manipulation.
- Dismissal thresholds must be predictable, and cancellation returns the surface to rest without jumping.

#### Feedback motion must be brief

Repeated controls should not make people wait. Use small changes in scale, opacity, elevation, symbol state, or position only long enough to acknowledge the action.

Default working ranges for Dyrane web and mobile products:

| Motion class | Typical range | Purpose |
|---|---:|---|
| Press acknowledgement | 60–120 ms | Immediate tactile response |
| State substitution | 120–200 ms | Selection, toggle, local status |
| Local disclosure | 160–260 ms | Expand, collapse, inline detail |
| Pane or sheet transition | 220–380 ms | Spatial layer change |
| Major route continuity | 260–450 ms | Preserve object or page topology |
| Expressive moment | 400–700 ms | Rare onboarding or meaningful completion |

These are starting ranges, not universal constants. Perceived distance, changed area, input velocity, and platform conventions determine the final value.

#### Motion must be interruptible

- Navigation becomes interactive as soon as the destination is stable enough to use.
- A second user action may reverse, continue, or supersede an in-progress transition.
- Do not lock input merely to protect decorative animation.
- Long-running work is represented by actual state rather than a blocking animation.

#### Frequent interaction receives less animation

The more often an action occurs, the less ceremonial its feedback should become. High-frequency finance entry, filtering, list selection, and operator workflows favor immediate state substitution over large transitions.

#### Reduced motion preserves meaning

When reduced motion is requested:

- replace large movement with opacity or instant state changes;
- remove parallax, oscillation, zoom, and background drift;
- keep state confirmation visible;
- preserve hierarchy and destination context;
- never make animation the only carrier of success, failure, progress, or selection.

### Motion anti-patterns

- staggered entrances on every page load;
- continuous ambient movement behind task content;
- bounce used as a universal personality layer;
- route transitions that ignore navigation direction;
- skeleton shimmer that becomes visually dominant;
- success confetti for routine actions;
- blocking animation before content becomes usable;
- large zoom transitions without a stable object relationship;
- motion that restarts whenever data refreshes;
- hover effects that cause layout movement.

## Interaction adaptation

### Immediate acknowledgement

Every direct manipulation must acknowledge input without waiting for network completion.

Examples:

- pressed or active state on pointer down or touch contact;
- local pending state after submission;
- drag surface tracking during movement;
- visible focus when reached by keyboard;
- selected state appearing before dependent data finishes loading.

### Standard gestures retain standard meaning

- tap or click activates or selects;
- drag moves or reveals an explicitly draggable surface;
- swipe supplements, not replaces, a visible action;
- pinch is reserved for spatial scale where appropriate;
- scroll remains scroll and is not silently overloaded;
- edge gestures must not conflict with platform navigation.

### Alternate paths are mandatory

Any core action exposed through hover, swipe, drag, long press, or context menu also needs an accessible visible or keyboard-reachable path.

### Gesture completion must be predictable

A direct manipulation defines:

- start condition;
- live feedback;
- threshold or destination;
- cancellation behavior;
- completion feedback;
- keyboard or button alternative.

### Destructive interactions

Interruption level must match consequence:

- reversible removal: act immediately and offer undo;
- expected deletion with low consequence: lightweight confirmation may be unnecessary;
- unexpected or irreversible data loss: explicit confirmation is required;
- bulk, account-level, financial, safety, or identity consequences: show scope and result before commitment.

## Feedback adaptation

Apple distinguishes passive status, meaningful completion, warnings, and critical interruption. Dyrane UI formalizes this into a feedback ladder.

### Level 0 — inherent control feedback

The control visibly changes during interaction.

Examples: pressed state, selected state, drag position, focus ring.

### Level 1 — local passive status

Persistent or quietly updated status appears beside the object it describes.

Examples: sync state, last updated time, assignment state, offline marker, validation hint.

### Level 2 — local action result

A mutation surface displays pending, success, or recoverable failure in context.

Examples: save button changes state; row shows retry; imported statement displays reconciliation result.

### Level 3 — transient cross-context confirmation

A toast or banner confirms a meaningful result that may otherwise be missed. It supplements local truth and should not be the only record.

### Level 4 — interruptive warning

An alert or blocking sheet is reserved for information requiring a decision before safe continuation.

### Level 5 — terminal boundary

Irreversible, identity-level, safety-critical, financial, or destructive consequences require explicit scope, clear action labels, and a recovery statement where applicable.

### Feedback rules

- Match interruption to consequence.
- Place feedback near the affected object whenever possible.
- Confirm significant completion, not every expected success.
- Explain failure in terms of result and next action.
- Do not rely on color, sound, vibration, or animation alone.
- Avoid generic messages such as “Something went wrong” when the system knows the failed boundary.
- Distinguish empty data from failed data retrieval.
- Keep persistent truth in the interface after transient feedback disappears.

## Accessibility adaptation

Current Apple guidance emphasizes perceivability, adaptability, multiple modalities, sufficiently sized controls, text scaling, contrast, simple gestures, gesture alternatives, and assistive-technology support.

Dyrane baseline:

- interactive touch targets aim for 44×44 CSS pixels or equivalent on touch-first surfaces;
- compact desktop controls may be visually smaller but retain adequate hit area and spacing;
- text can scale without clipping, overlap, or loss of action;
- information never depends on color alone;
- custom controls expose names, roles, values, and states;
- keyboard focus is visible and follows task order;
- drag and swipe actions have button or menu alternatives;
- error messages are associated with their fields and announced where appropriate;
- reduced motion is treated as a functional mode;
- sound or haptic feedback supplements visible state;
- charts provide textual summaries or accessible equivalents.

## Dyrane-specific divergence from Apple aesthetics

Dyrane UI may align with Apple’s human-factors guidance without adopting every visual fashion.

Dyrane products generally prefer:

- borderless tonal hierarchy over universal glass containers;
- selective translucency rather than pervasive material effects;
- product-specific semantic signals rather than decorative system color;
- restrained typography with stronger data density where operationally necessary;
- web-native responsiveness rather than direct simulation of native navigation;
- contextual intelligence and evidence surfaces beyond standard platform components.

The canon should feel native to its product and platform, not like an Apple screenshot recreated in React.
