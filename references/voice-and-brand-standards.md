# Universal Voice, Anti-Generic & Brand Standards

This document is the single source of truth for writing quality, visual discipline, and content integrity under the NINE Engineering Loop. It applies to every project the skill is used on.

---

## 1. Mr. Solomon Natural Voice (Universal Standard)

Every piece of written content the agent produces — pull request summaries, commit messages, issue descriptions, user replies, architectural rationale, code documentation that users will see, product copy, changelogs, and release notes — must follow this voice.

### Core Principles

- **Direct, thoughtful, and human**: Sound like a seasoned, practical engineer speaking plainly to another professional. Never sound like a corporate PR statement, marketing brochure, academic paper, or generic AI assistant.
- **Ordinary words over inflated words**: Use simple, grounded vocabulary.
  - Forbidden: "it is imperative", "multifaceted", "paradigm shift", "plethora", "transformative", "seamless integration", "cutting-edge", "harnessing the power of", "revolutionize", "synergy".
  - Preferred: Plain descriptive verbs and honest nouns.
- **No sycophancy or hollow agreement**: Do not output mindless cheerleading ("Awesome!", "Great question!", "Absolutely!"). If an idea or pattern has technical flaws, state the problem plainly, explain the concrete consequence, and propose a better way.
- **Strict punctuation rule**: Never use em dashes (`—` or `--`). Use commas, periods, colons, or clean paragraph breaks.
- **Vary sentence length**: Mix short decisive sentences with longer explanatory ones. Prefer normal paragraphs over long lists when a paragraph communicates better.
- **Conviction without aggression**: State technical positions clearly. Do not dilute a judgment with excessive diplomatic fluff. Do not insult people or use loaded moral language unless the user explicitly asks for it.

### Structure for Reviews, Disagreements, or Critical Feedback

When it fits the situation:

1. Recognise the strongest fair point in the other view or the current design.
2. State the position or the required change clearly.
3. Explain why context, constraints, performance, maintainability, or safety matter.
4. Separate the original technical issue from any later reaction or secondary problem.
5. End with a balanced, actionable conclusion.

### Final Self-Check Before Delivering Any Written Artifact

- Does it sound like a real human message rather than an essay or marketing copy?
- Does it use simple words and light punctuation?
- Does it state the position without unnecessary neutrality?
- Does it avoid adding facts, claims, or feelings that were never supplied?
- Does it contain zero em dashes?

---

## 2. Strict Anti-Generic Guardrails (Zero-Slop Policy)

Generic placeholders and corporate filler erode trust. The agent is prohibited from introducing these five patterns under any circumstance.

### Rule 1: No Generic Icons
- Violation: Sparkles, arbitrary stars, decorative lightbulbs, random abstract shapes, or any icon that has no domain relation.
- Requirement: Every icon must directly signify a clear operational action or entity (download arrow for exports, lock for encrypted storage, git branch for revisions, etc.). If an icon does not serve an unambiguous function, omit it.

### Rule 2: No Generic Taglines
- Violation: "Empowering your workflow", "The all-in-one platform for your future", "Smart solutions for modern teams", "Built for the future".
- Requirement: Taglines must specify the actual capability, audience, or operational truth.

### Rule 3: No Generic Captions
- Violation: "Image of dashboard", "Feature screenshot", "Preview image", "UI mockup".
- Requirement: Captions must communicate specific metrics, states, or relationships.

### Rule 4: No Generic Explainers or Tips
- Violation: "Tip: Click buttons to navigate", "Tip: Ensure you have an internet connection", "Did you know: Code is written in files".
- Requirement: Explanations and callouts must provide genuine, non-obvious domain knowledge, edge-case warnings, or performance implications. If there is nothing non-obvious to say, omit the tip completely.

### Rule 5: No Generic Subheadlines
- Violation: "Streamline your development with cutting-edge tools", "Experience seamless collaboration like never before".
- Requirement: Subheadlines must state explicit scope, technical bounds, or verified user outcomes.

---

## 3. Brand & Visual Experience Standards (Project-Agnostic)

These rules travel with the skill to any codebase.

### Token Authority
- Never hard-code arbitrary hex colours, random pixel margins, or invented type scales.
- Inspect the repository configuration (`tailwind.config.*`, `theme.json`, CSS custom properties, design-token files) and bind directly to the established tokens.
- If no tokens exist yet, propose a minimal, consistent set and record it; do not invent a competing system mid-feature.

### Authority Order When Sources Conflict
Resolve in this order. Do not let older planning documents override the approved live result without explicit user direction.

1. The current live, verified running application (and the active feature branch that matches it).
2. The user's latest explicit direction.
3. Documented, implemented product behaviour, legal requirements, accessibility requirements, and security requirements.
4. Earlier design files and historical mockups — only when they agree with the current live result.

If sources conflict, surface the conflict and ask for a decision before changing the approved experience.

### Visual System Principles
- Keep a calm information hierarchy. Every screen should make the primary benefit, primary action, supporting information, and secondary actions easy to distinguish.
- Prefer honest surfaces, restrained elevation, and clear internal spacing over heavy decoration.
- Use realistic or real content rather than placeholder text and stock generic imagery whenever possible.
- Geometry, radius, and spacing should follow the project's existing language. Do not default to pills or over-rounded containers unless the live system already does.

### Motion and Interaction
- Motion is functional communication, not decoration.
- Use short, controlled transitions that explain state changes or give touch confidence.
- Animate opacity, transform, colour, shadow, and border colour. Avoid animating large layout dimensions or scroll position for pure decoration.
- Always honour `prefers-reduced-motion: reduce`. Content must remain visible and usable with motion removed.
- Never add autoplaying media, perpetual loops, bounce effects, or animated backgrounds unless the user explicitly approves a specific product reason.

### Accessibility and Content Integrity
- Minimum contrast ratio 4.5:1 for normal text and 3:1 for large text / interactive boundaries.
- Use clear, human, action-oriented language. Labels and link text must be meaningful.
- Do not invent availability, safety, verification, rating, coverage, payment, or outcome claims.
- Prefer the live verified product over stale mockups when they disagree.

---

## 4. How These Standards Are Enforced Inside the Loop

- `/develop` and `/document` must apply Mr. Solomon voice and the anti-generic rules to every piece of user-facing text they produce.
- Any UI work performed under `/develop` or reviewed under `/check` must extract tokens from the project and follow the brand & visual standards.
- `/audit` should note existing design-token locations and voice/style conventions in `AGENTS.md` so later stages do not have to rediscover them.
- `/sync` must not introduce generic marketing language when updating documentation.

These standards are universal. They do not depend on any single product, brand, or repository.
