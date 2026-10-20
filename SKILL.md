---
name: design-skill
description: Design or substantially redesign websites, apps, screens, and interactive prototypes through visual references, user-approved layout choices, a concrete specification, and screenshot verification. For small styling fixes, apply only relevant quality checks.
---

# Design Skill

Use these instructions when designing or substantially redesigning a website, app, screen, or interactive prototype. Do not apply the full exploration workflow to tiny styling fixes.

This playbook is an original Codex-oriented adaptation of Anshu Chimala’s *How to turn your AI into a world-class designer*. It translates the article’s Discover → Define → Deliver approach into an executable workflow and adds production, accessibility, security, and stopping rules.

Source: https://www.lennysnewsletter.com/p/how-to-turn-your-ai-into-a-world

## Mission

Create a product-specific design with a clear point of view. Avoid the safest average of common AI-generated interfaces. Distinctiveness must support the product’s purpose; it must not reduce usability, accessibility, responsiveness, or performance.

## Operating principles

- Begin with the user, product, and emotional goal—not visual effects.
- Explore several genuinely different concepts before polishing one when the direction is still open.
- Make each important visual choice intentional and explainable.
- Use references as a quality bar and moodboard, never as a layout to copy.
- Prefer a single strong visual idea over a pile of fashionable effects.
- Treat restraint as part of the design. Remove elements that do not help users understand, decide, or act.
- For a focused task, give the screen one clear job and one visually dominant next action. Reveal secondary detail when it becomes useful.
- Show visual references before proposing a new direction. Present one consequential design decision at a time and preserve approved choices.
- Use native or design-system components when they are stronger than custom replacements.
- Keep secrets out of prompts, source code, screenshots, logs, and committed files. Prefer built-in media tools; never request that an API key be pasted into chat.

## Phase 0: Understand the assignment

Before designing, identify or infer:

- Product and page/screen purpose
- Primary audience and the action they should take
- Required content, states, and workflows
- Brand constraints and existing design-system rules
- Platform, framework, assets, and technical constraints
- Responsive targets and accessibility requirements
- What the design should feel like—and what it must avoid

Ask only for missing information that would materially change the result. If the request is sufficiently clear, state brief assumptions and proceed.

Choose one working mode:

1. **Explore** — the visual direction is open; generate alternatives before building deeply.
2. **Refine** — a direction or reference already exists; preserve its intent and improve execution.
3. **Ship** — the design is approved; focus on completeness, responsive behavior, accessibility, and polish.

## Phase 1: Discover

### 1. Show references before designing

When establishing a new direction, gather two to four relevant existing websites or UI images before proposing original concepts. Use supplied references first. Show the actual reference images or screenshots inline in the conversation when the environment supports it; links alone are not a visual review. Include a source link and a short explanation of the layout, hierarchy, or interaction principle each reference demonstrates.

Use available browsing, screenshot, and image-preview tools. If previews cannot be displayed, say so and provide the best available source links; do not imply the user has seen a visual. Do not make up reference screenshots or present generated concepts as existing products.

Use references as inspiration, not permission to copy a site's content, assets, or exact composition. Keep the set focused on the current decision. For a refinement with an approved reference, reuse it instead of restarting discovery.

### 2. Define the design target

Write a compact internal brief containing:

- The desired user response or emotion
- The central visual idea
- Three to five qualities to emphasize
- Three to five patterns to avoid
- The first viewport’s composition and primary action
- The one thing a user should accomplish on each focused screen
- What must be visible now, what can wait until requested, and what can be removed

Avoid empty adjectives such as “modern,” “clean,” or “premium” unless they are tied to concrete choices.

### 3. Choose layout before visual details

When in Explore mode, show three distinct layout options before substantial implementation. Use lightweight wireframes, layout sketches, or visual mockups displayed inline; prose alone is not a layout preview. Keep content and fidelity comparable so the user can judge structure. Vary dimensions such as:

- Information hierarchy and first-viewport composition
- Density and use of negative space
- Placement and prominence of imagery, data, or a product demo
- Navigation and interaction model
- Grouping, reading order, and progression through the task

Keep palette and typography broadly consistent during the layout comparison. Explore their character, media treatment, and motion later if those decisions remain open.

For each direction, state:

- The idea in one sentence
- Why it fits the product and audience
- Its most memorable design decision
- Its main usability or implementation risk

Explain each option's tradeoff, recommend the strongest fit, then let the user choose the layout before building it deeply. Do not bundle layout, palette, typography, and motion into one approval request. After layout is settled, resolve the next consequential open decision; routine implementation details do not need repeated approval.

Do not build all three directions fully unless requested. If the user explicitly delegates the choice, select a direction and record the reasoning. In Refine or Ship mode, preserve the approved layout and skip new alternatives unless the user asks to revisit it.

### 4. Optional entropy seed

Use this only when the user wants broad exploration and the initial concepts keep converging on familiar patterns.

1. Generate a random seed outside the language model, for example with `openssl rand -hex 24` or `uuidgen`.
2. Interpret structural features of the seed as private creative constraints for layout, rhythm, palette, typography, or motion.
3. Keep only interpretations that support the brief.
4. Do not display the seed or encode it literally in the interface.

Randomness is an ideation catalyst, not a reason for arbitrary design.

### 5. Keep a decision record

Maintain a compact record of the chosen references, approved layout, liked qualities, rejected patterns and reasons, and unresolved questions. Carry it forward through the specification, implementation, and critique. When working in a repository, use an existing design brief or a concise `design-decisions.md` so choices survive a later session; otherwise keep a clear summary in the conversation.

Treat preferences as scoped to this product unless the user asks to generalize them. Do not reopen settled decisions or quietly reintroduce rejected patterns. Revisit a choice only when the user requests it or a concrete constraint makes it unworkable; explain the constraint and propose the smallest necessary adjustment.

## Phase 2: Define

### 1. Set the screen's attention budget

Before adding sections or components, describe the screen's job in one sentence and identify its next meaningful action. For a focused action such as creating, uploading, booking, or starting something, begin with the minimum complete interface: a clear title, the essential inputs or context, and one dominant action.

- Keep information visible only when it helps the current decision. Move advanced settings, optional explanations, and infrequent actions behind clear, accessible disclosure controls.
- Use short, concrete labels and action verbs. Remove repeated instructions, introductory paragraphs, and helper text that restates the label. Retain guidance needed to prevent errors or explain consequences.
- Prefer sensible defaults. Ask for information only when it is needed; keep related, easy fields together.
- Use sequential steps when later decisions depend on earlier ones or a single screen would be overwhelming. Do not turn a small form into a wizard simply to show one field at a time. Preserve entered data and make back/edit navigation clear.
- Keep essential costs, risks, permissions, errors, and recovery controls visible at the point of decision. Simplicity must not hide consequences or make necessary actions hard to find.
- Dashboards, comparison views, and expert tools may need several actions or dense information. Group by task, establish a clear hierarchy, and retain useful context instead of forcing every screen into a single-action template.

Read [references/simplicity.md](references/simplicity.md) when simplifying an overloaded screen or deciding between inline content, disclosure, and separate steps.

### 2. Create a build-ready design specification

Before substantial implementation, define:

- Approved references, layout, and decisions that must be preserved
- Page or screen hierarchy and the primary action for each focused screen
- Essential visible content, optional disclosures, and any step boundaries
- First viewport composition
- Color roles and contrast behavior
- Type roles, scale, and line lengths
- Spacing rhythm, grid, containers, radius, borders, and shadows
- Component inventory and interactive states
- Imagery or media direction
- Motion behavior and reduced-motion fallback
- Desktop, tablet, and mobile behavior
- Empty, loading, error, success, disabled, and focus states where relevant

Use existing project tokens and components when they fit. If new tokens are needed, define a small coherent system rather than scattered one-off values.

### 3. Implement the visual thesis first

Build the smallest complete slice that proves the chosen direction—usually the first viewport plus one representative content or interaction section. Verify it visually before expanding the pattern across the product.

### 4. Use media intentionally

Use image generation when bespoke imagery materially strengthens product storytelling, atmosphere, or comprehension. Use video or advanced motion only when it adds meaning or a memorable interaction that static media cannot provide efficiently.

- Prefer built-in image generation when available.
- Keep generated text out of images when the interface can render real text.
- Match crop, lighting, palette, perspective, and texture across assets.
- Provide useful alt text or mark decorative media appropriately.
- Compress and size assets for their display context.
- Do not add expensive media merely to make the page feel less empty.

### 5. Run an independent design critique when available

If fresh-context agent delegation is available and authorized, use a critic that sees only:

- Current screenshots at representative viewport sizes
- The product goal and chosen design direction
- The approved layout and relevant recorded preferences
- Optional reference images used as a quality bar

Do not show the critic source code, implementation rationale, previous critiques, or sunk effort.

Ask the critic to evaluate:

- Product fit and clarity
- Whether the main action is obvious without reading explanatory paragraphs
- Unnecessary decisions, competing actions, or content that can wait
- Faithfulness to the approved layout and recorded preferences
- Composition and hierarchy
- Typography, spacing, and consistency
- Originality versus familiar AI patterns
- Interaction affordances and state clarity
- Accessibility and responsive risks visible in the screenshots
- The three highest-impact improvements
- A 1–10 quality score with concrete reasons

Use the score diagnostically, not as truth. Apply only feedback that improves the agreed brief.

Default stopping rule: run at most two critique-and-revision rounds. Continue only when each round makes measurable progress and no regression is introduced. A high score is not a substitute for acceptance criteria.

## Phase 3: Deliver

### 1. Remove what does not earn its place

For every section, container, label, decoration, and animation, ask:

- Does it improve comprehension, hierarchy, trust, action, or emotional impact?
- Is the same job already being done by another element?
- Would the interface become clearer if this were removed or merged?
- Does this need to be visible before the user takes the main action?
- Is the page asking for more decisions or reading than the task requires?

Delete redundant copy, wrapper cards, decorative badges, unnecessary dividers, repeated CTAs, fake metrics, and effects without a product purpose. Do not fill empty space just because it is available. Distinctiveness can come from typography, proportion, spacing, or one meaningful visual.

Run a brief clarity check: can a new user tell what this screen is for and what to do next without reading a paragraph? If not, simplify the hierarchy and wording before adding more explanation.

### 2. Check for common AI-design tells

Treat this as a diagnostic list, not a universal ban:

- Default purple/blue gradients unrelated to the brand
- Glow effects, glass panels, or blurred blobs used as automatic decoration
- A generic split hero with text left and an abstract graphic right
- Too many rounded cards or pills nested inside other cards
- Random accent colors with no semantic role
- Oversized headings paired with vague marketing copy
- Decorative charts, testimonials, logos, metrics, or badges that are invented or unsupported
- Uniform grids that ignore content importance
- Excessive microcopy that explains what the visual hierarchy should already communicate
- Custom controls that are less clear or usable than platform-native controls
- Animation everywhere instead of motion reserved for hierarchy, feedback, or continuity

Keep stylistic patterns when the brief justifies them and the execution is specific. Never present invented metrics, testimonials, customer logos, or other unsupported claims as real.

### 3. Production-quality visual QA

Render and inspect the actual implementation rather than judging code alone.

Check at minimum:

- Mobile, tablet, and desktop screenshots, including the initial viewport
- Faithfulness to the approved layout, references, and recorded decisions
- A clear primary action with no unnecessary competing emphasis
- Disclosures and step navigation that remain usable with keyboard and on small screens
- No overflow, overlap, clipping, or unintended layout shift
- Legible type, sensible line lengths, and consistent spacing
- Keyboard navigation and visible focus states
- Color contrast and non-color state indicators
- Hover, active, disabled, loading, empty, error, and success states
- Reduced-motion behavior
- Real content stress cases, including long text and missing media
- Image sharpness, cropping, loading behavior, and file weight
- Console errors and obvious performance regressions

Fix the largest visible or functional gaps, then re-render and inspect again.

## Definition of done

The work is complete when:

- The interface has one coherent, product-specific visual idea.
- The primary user goal is obvious in the first viewport or initial screen.
- Focused screens expose only what is needed for the current decision, with optional detail easy to discover.
- Copy is concise without losing essential guidance or consequences.
- The implementation follows the approved direction and does not reintroduce rejected patterns.
- Visual choices follow a consistent system rather than isolated styling.
- Unnecessary elements and unsupported content have been removed.
- Representative responsive screenshots have been reviewed.
- Essential interaction states, accessibility, and reduced-motion behavior work.
- The implementation passes the project’s relevant checks.
- Remaining limitations and asset needs are stated plainly.

## Expected handoff

When reporting completion, include:

- The chosen direction and why it fits
- The most important design decisions
- What was removed or simplified during polish
- The decision record and any justified departures from the approved direction
- Representative screenshots displayed inline when supported
- Viewports and interaction states verified
- Tests or checks run
- Remaining limitations, if any
