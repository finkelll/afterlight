---
stepsCompleted: ['step-01-init', 'step-02-discovery', 'step-03-core-experience', 'step-04-emotional-response', 'step-05-inspiration', 'step-06-design-system', 'step-07-defining-experience', 'step-08-visual-foundation', 'step-09-design-directions', 'step-10-user-journeys', 'step-11-component-strategy', 'step-12-ux-patterns', 'step-13-responsive-accessibility', 'step-14-complete']
inputDocuments:
  - _bmad-output/planning-artifacts/prd.md
  - _bmad-output/planning-artifacts/product-brief-ai-2026-03-01.md
  - _bmad-output/planning-artifacts/research/market-virtual-memorial-platforms-and-online-remembrance-products-like-afterlight-research-2026-03-01.md
  - _bmad-output/planning-artifacts/research/technical-architecture-and-stack-for-afterlight-research-2026-03-01.md
---

# UX Design Specification – Afterlight

**Author:** Finkel
**Date:** 2026-03-06

**Document purpose:** This is an **instructional base for designers and developers**, not the final pixel-level design. It defines direction, principles, palette, patterns, and copy so that high-fidelity mockups and implementation can be created from it. Treat it as the single source of truth for intent; the “final” design is what gets built or produced in design tools from this spec.

---

## Terminology (product language)

Use these terms consistently in UI, copy, and documentation.

| Concept | Term | Definition |
|--------|------|------------|
| **Main space** | **Room** | The whole memorial for one person who has died. One room per person. Contains that person's intro (image, optional details), and all Moments and Tributes. |
| **Themed container (type 1)** | **Moment** | A container for **sharing a memory or a moment** you had with that person. Focus: personal recollection, story, or shared experience (e.g. "Her laugh," "Stories we tell," "A trip we took"). Candles here = "I remember…" / "A moment we shared." |
| **Themed container (type 2)** | **Tribute** | A container for **dedicating something to or for** that person. Focus: offering, dedication, or gift in their honor—e.g. a song, a flower, a candle (ritual), a prayer, or a **link** (video, article, etc.) you're sharing for them. Candles here = "This is for you" / "I'm dedicating this to them." |
| **Single contribution** | **Candle** | One person's contribution inside a Moment or Tribute: text (required) + optional photo or **link** (URL to a video, article, or other resource). |
| **Primary action** | **Light** | Main CTA label (e.g. button "Light"). Longer copy: "Light a candle" or "Add your light" where it reads well. |

**Hierarchy:** Room → Moments and Tributes (two container types) → Candles. A room can contain both Moments and Tributes. Avoid "thread" (conflict with Threads); avoid "space" for main space (MySpace).

**Moment vs Tribute (when to use which):**
- **Moment** = "I'm sharing a memory or moment *with* them" — something that happened, a story, a feeling you had together. Organizer creates Moments like "Her laugh," "What she taught us," "Stories we tell."
- **Tribute** = "I'm dedicating something *to* them" — an offering, a song, a link to a video or article, a prayer, a flower. Organizer creates Tributes like "A song for her," "Videos we're sharing for him," "Prayers and dedications."

**Important: the Moment vs. Tribute distinction is organizer-facing scaffolding.** It helps the organizer create a meaningful structure, but for contributors the distinction is low-stakes. Any candle in any container is welcome and valid — the system does not enforce or correct placement. If someone puts a dedication in a Moment or a memory in a Tribute, that's fine. Contributor-facing copy leans into this: "Share whatever feels right."

---

<!-- UX design content will be appended sequentially through collaborative workflow steps -->

## Executive Summary

### Project Vision

Afterlight is a shared memorial web app where families and friends create **rooms** for someone who has died and add **candles** (text required; optional photo or link) inside **Moments** (memories/moments with that person) or **Tributes** (dedications—e.g. song, flower, candle, prayer, or a shared link such as a video). The owner can set a main image of the person, optional details (e.g. first/last name, dates, places), and add photos and images to the room; contributors use the **Light** action to add a candle. The product vision is a calm, emotionally safe "home for memories" that supports ongoing shared remembrance over time. The model (Room → Moments & Tributes → Candles) and privacy-first, non-exploitative stance differentiate it from static tribute pages and ad-driven or noisy alternatives. The desired "aha" moment is when the organizer sees the first candle from someone else and feels the space is working as a shared home.

### Target Users

- **Family Organizer (primary):** Creates the room (main image of the person, optional details such as first/last name, dates of birth and passing, places of birth and death, and additional photos/images—all optional), sets visibility (public or link-only) and optional approval for new candles, uses "Copy link" and "Copy message" from room settings to share, and moderates (remove candle or Moment/Tribute). Wants minimal setup, confidence the space will last, and to see others contribute. Success = first non-creator candle and ability to re-share around anniversaries.
- **Contributor (primary):** Visits via the room URL, sees room intro (main image, optional details) and list of Moments and Tributes, reads candles, and adds candles via **Light** (text required; optional photo or link; name or "Someone"). Wants low friction, reassurance that short or anonymous contributions are valid, and the option to return later (e.g. anniversaries).

### Key Design Challenges

- **Emotional safety and cognitive load:** Grief-sensitive tone, pacing, and UX; no pressure or gamification; reassurance that short or anonymous contributions are enough.
- **Ritual-shaped IA:** Room → Moments and Tributes → Candles must be clear and understandable without feeling gimmicky; first-time and less tech-savvy users need clear wayfinding.
- **Contributor friction:** Minimize steps from link to **Light** (or "Light a candle") to confirmation; gentle copy and optional name/guest so contributors don't hesitate. The Moment vs. Tribute distinction is organizer scaffolding — contributors should feel any candle in any container is valid.
- **Moderation without heaviness:** Organizer controls (remove candle or Moment/Tribute, optional approval) must be available but unobtrusive so the space feels like a memorial first.
- **Mobile-first and accessibility:** Touch targets, readability, performance; WCAG 2.1 AA for core flows (room view, Moment/Tribute view, Light (add candle), room creation, moderation).

### Design Opportunities

- **Light as hero action:** Primary CTA label **"Light"** (longer copy: "Light a candle" or "Add your light"). Single clear CTA from room and from each Moment/Tribute; gentle, permission-giving copy; simple form (text first; optional photo or link attachment).
- **Room, Moments, and Tributes as calm hierarchy:** Room as "home" (main image of the person, optional details e.g. name/dates/places, owner-added photos); Moments = memories/moments with that person; Tributes = dedications (song, flower, candle, prayer, or shared link e.g. video). Subtle activity cues without engagement metrics.
- **Candles spread, not aggregated:** Candles are shown individually (spread), not as a single aggregated count. Each candle displays the name of the person who lit it and, when provided, the sentence or message they wrote. Moment/Tribute view is a list of individual candles (name + message per candle), with pagination/lazy-load as needed.
- **Trust and clarity:** Plain-language visibility and approval settings; room URL is the shareable link, with "Copy link" and "Copy message" helpers in room settings for easy re-sharing.
- **Return visits:** Same URL, recognizable room, optional gentle cues that the space is still here for anniversaries and revisits.

## Core User Experience

### Defining Experience

The core experience is defined by one primary action: **Light** (button; longer copy "Light a candle" or "Add your light"). Contributors add a candle (text required; optional photo or link) to a Moment or Tribute within a room. For the Family Organizer, the parallel critical flow is **create room → copy link → share** so others can visit and contribute. The product delivers value when lighting a candle is obvious, low-friction, and emotionally safe—supported by a clear hierarchy (room as home, Moments and Tributes as containers, candles as contributions) and no unnecessary steps or pressure.

### Platform Strategy

- **Web-first, mobile-friendly:** Primary access is via the room URL on phone or desktop. All core flows (room view, Moment/Tribute view, Light (add candle), room creation, moderation) must work from ~320px to desktop.
- **Touch and pointer:** Touch targets and readability prioritized for grief-sensitive use on phones; keyboard and mouse fully supported for accessibility and desktop.
- **No native app or offline for MVP:** Connectivity assumed; progressive enhancement where feasible (e.g. form submit without JS or graceful degradation).

### Effortless Interactions

- **Land on room:** Open link → immediately see who the room is for, a short line, and the list of Moments and Tributes (with subtle candle counts). No signup or login required to view.
- **Light:** One clear CTA ("Light") from room and from each Moment/Tribute; gentle, permission-giving copy; simple form (text first; optional photo or link; name or "Someone"); minimal steps to submit and see confirmation.
- **Create and share (organizer):** Create room with main image, optional details (name, dates, places), optional photos/images, and starter Moments and/or Tributes → room URL is created; use "Copy link" and "Copy message" from room settings to share; re-share same URL anytime.

### Critical Success Moments

- **Organizer:** Sees the first candle from someone other than themselves → realizes the space is working as a shared home.
- **Contributor:** Submits a candle → sees clear confirmation ("Thank you. Your candle is now part of this [moment/tribute]") and their candle in the list; feels they did something meaningful without it being a big production.
- **Return visit:** Same URL, recognizable room, space still available for anniversaries or when thinking of the person—no re-onboarding, no clutter.

### Qualitative Validation (UX-specific)

- **Post-contribution pulse:** After a contributor lights a candle and sees the confirmation, the in-page confirmation area includes an optional, single-question prompt (e.g. "Did this feel right?" with simple yes/not-really). Non-intrusive; never repeated in the same session. Styled to match the calm tone — not a survey popup.
- **First-contributor experience observation:** The empty-state-to-first-candle flow is the highest-stakes UX moment. Use session replay (with consent) to watch how first contributors interact with the empty state copy, how long they hesitate, and whether the reassurance prompts help.
- **Organizer sentiment after first candle:** After the first non-creator candle, prompt the organizer once (e.g. "How is the space feeling so far?") — brief, optional, in context.

### Experience Principles

- **One hero action:** **Light** (or "Light a candle") is the primary CTA; room and Moment/Tribute structure exist to make this action discoverable and meaningful.
- **Calm and minimal:** No gamification, counts, or engagement prompts; short or anonymous contributions are explicitly valid; tone is grief-sensitive.
- **Ritual clarity:** Room → Moments and Tributes → Candles is the mental model; navigation and hierarchy make this obvious without explaining the metaphor.
- **Trust and control:** Visibility (link-only vs public) and approval settings in plain language; room URL with "Copy link" and "Copy message" helpers so organizers can re-share with confidence.

## Desired Emotional Response

### Primary Emotional Goals

- **Emotionally safe and held:** Users should feel the product is a calm, respectful place—no pressure, no judgment. The space supports grief rather than adding cognitive or emotional load.
- **That what they shared was enough:** Contributors should feel their candle (short, anonymous, or long) is valid and welcome. Copy and flow reinforce that there is no "right" way to contribute.
- **The space is working (organizer):** When others add candles, the organizer should feel relief and quiet satisfaction that the memorial is a real shared home, not a one-off page.

### Emotional Journey Mapping

- **First discovery (organizer):** Tired, sometimes skeptical—hoping something will be simple and lasting. Onboarding should reduce doubt and effort so they feel "I can do this."
- **First discovery (contributor):** Lands via link; may feel unsure what to write or whether their note is "enough." Room and Moment/Tribute intro plus gentle "Light a candle" copy should build permission and reduce hesitation.
- **During core action (light a candle):** Calm focus—simple form, reassurance that short or anonymous is fine; no sense of being on display or performing.
- **After contributing:** Brief confirmation and seeing their candle in the list → "I did something meaningful without it being a big production"; included in shared remembrance.
- **When something goes wrong:** Moderation (remove candle) should feel like restoring safety, not punitive. Errors or limits (e.g. upload) should be explained simply, without blame.
- **Return visit:** Same room, same URL—familiar and still available; "this is still here for me" without re-onboarding or clutter.

### Micro-Emotions

- **Confidence over confusion:** Clear hierarchy (room → Moments and Tributes → candles) and one obvious CTA ("Light") so users know where they are and what to do.
- **Trust over skepticism:** No ads, no selling of data, plain-language privacy and control; room URL and approval settings in the open so organizers feel in control.
- **Permission over anxiety:** Explicit reassurance that short or anonymous contributions are enough; no character minimums or "engagement" pressure.
- **Quiet belonging over isolation:** Seeing others' candles and adding one's own should feel like being part of a shared remembrance, not performing for an audience.
- **Accomplishment without pressure:** Contributor completes a small, meaningful act; organizer sees the space being used—satisfaction without gamification or hype.

### Design Implications

- **Calm and safe:** Soft palette, generous spacing, no auto-play or aggressive motion; copy is warm, concise, and permission-giving (e.g. "There's no right way… Whatever you share is enough").
- **Low pressure:** No counts, streaks, or "engagement" prompts; optional name/"Someone"; no mandatory signup to contribute.
- **Trust and control:** Visibility and approval explained in plain language; room URL with "Copy link" and "Copy message" helpers easy to find and re-share; moderation (remove candle or Moment/Tribute) available but unobtrusive.
- **Clarity and inclusion:** One hero CTA (Light); confirmation message that names the outcome ("Your candle is now part of this [moment/tribute]"); room and Moment/Tribute structure make "where I am" and "what I can do" obvious.

### Emotional Design Principles

- **Safety first:** Tone, pacing, and UI minimize stress and cognitive load; the product never feels exploitative or noisy.
- **Permission over prescription:** Reassure that any contribution is valid; support short, anonymous, or longer candles equally.
- **Quiet connection:** Design for shared remembrance and return visits (e.g. anniversaries) without turning the space into a feed or social stage.
- **Trust through transparency:** Clear control over visibility and approval; no dark patterns; sharing and re-sharing flows support organizer confidence.

## UX Pattern Analysis & Inspiration

### Inspiring Products Analysis

- **Invite-link, low-friction contribution (e.g. shared forms, docs):** Open link → see context → contribute with minimal or no account. **Lesson:** Link-first access, optional name/guest, copyable message support organizer re-share and contributor ease.
- **Calm, focused writing (e.g. journaling/reflection apps):** Soft visuals, no feeds, one primary action. **Lesson:** Single hero CTA ("Light a candle"), gentle copy, no gamification or engagement metrics.
- **Themed structure without feeds (e.g. topic-based forums/boards):** Clear hierarchy of place → topic → entry. **Lesson:** Room → Moments and Tributes → Candles as the core IA and mental model; wayfinding without feed mechanics.
- **Trust and control (e.g. link-only sharing, clear visibility):** Users see who can access and how. **Lesson:** Plain-language visibility (link-only vs public) and approval settings; room URL with "Copy link" and "Copy message" helpers.

### Transferable UX Patterns

- **Navigation:** One-level-down from room (list of Moments and Tributes with optional count per Moment/Tribute) and one-level into a Moment or Tribute (candles spread: each candle shown with author name and message). No aggregation that hides individual candles; Moment/Tribute view = list of individual candles (name + sentence each), with pagination/lazy-load. **Light** available from room and from within each Moment or Tribute.
- **Interaction:** Single primary action per context; optional secondary (e.g. add photo or link) after text; confirmation that states outcome ("Your candle is now part of this [moment/tribute]").
- **Visual:** Soft palette, generous spacing, readable type; no auto-play or aggressive motion; optional candle/light visual metaphor used sparingly to support ritual feel without kitsch.

### Anti-Patterns to Avoid

- **Static one-way pages:** Design for return visits and ongoing contribution; room and Moments/Tributes should feel like a living space, not a single post.
- **Feed or social mechanics:** No likes, counts, streaks, or "engagement" prompts; avoid infinite scroll or algorithm-driven order where it undermines calm.
- **Heavy signup or opaque permanence:** No mandatory account to view or contribute; clarity on retention/export so families don't fear the platform disappearing.
- **Gimmicks or replacement narrative:** No AI avatars, chatbots, or framing that suggests "talking to" the person; focus on shared remembrance among living people.

### Design Inspiration Strategy

- **Adopt:** Link-first access and copyable share message; one hero CTA; Room → Moments and Tributes → Candles IA; plain-language visibility and approval; confirmation copy that names the outcome; soft, calm visual direction.
- **Adapt:** Themed-container pattern (Moments and Tributes) adapted to memorial context (starter Moments and Tributes at room creation); optional name/guest to balance attribution and low friction.
- **Avoid:** Feeds, gamification, mandatory signup for contribution, opaque "forever" claims, AI/replacement framing; keep ritual metaphor meaningful but not literal or heavy-handed.

## Design System Foundation

### Design System Choice

**Themeable design system** — Use a themeable UI foundation (e.g. utility-first CSS such as Tailwind plus a component set, or a themeable component library such as Chakra UI or MUI) so the product can achieve a calm, soft, grief-appropriate visual language while keeping development speed and consistency. Avoid a fully custom system (too costly for MVP) and a single rigid established system (e.g. default Material) that would fight the desired emotional tone.

### Rationale for Selection

- **Emotional and brand fit:** Calm, soft palette and generous spacing need to be first-class; a themeable system allows custom tokens (color, type, spacing) without building every component from scratch.
- **Speed and team size:** Small team and MVP scope benefit from shared components, accessibility defaults, and documentation; a themeable library delivers that while still allowing strong customization.
- **Accessibility:** WCAG 2.1 AA is required for core flows; choosing a system with solid a11y defaults (focus, labels, contrast) reduces risk and rework.
- **Platform:** Web and mobile-friendly layout and touch targets are easier with a responsive, themeable component set and design tokens.

### Implementation Approach

- **Design tokens:** Define a small set of tokens for color (soft, low-saturation palette), typography (readable, calm type scale), and spacing (generous padding/margins) that reflect the emotional design principles.
- **Component layer:** Use the chosen library's components as a base; override or extend only where needed for tone (e.g. buttons, cards, form inputs) so the UI feels calm and non-gamified.
- **No heavy motion or auto-play:** Use system defaults for transitions sparingly; avoid animations that distract or feel "product-y"; prefer subtle, purposeful feedback (e.g. confirmation after lighting a candle).

### Customization Strategy

- **Adopt:** Responsive grid, form patterns, focus and keyboard behavior, and baseline accessibility from the chosen system.
- **Customize:** Color palette, type scale, border-radius, and shadow to support a soft, memorial-appropriate feel; primary CTA ("Light a candle") and room and Moment/Tribute cards as key custom expressions.
- **Avoid:** Default "tech" or high-contrast aesthetics; any component styling that feels loud, playful, or gamified.

## 2. Defining Core Experience

### 2.1 Defining Experience

The defining experience for Afterlight is **Light a candle**: a contributor adds a memory or tribute (text required; optional photo or link) to a Moment or Tribute inside a room. This is the one interaction that, if we get it right, makes the product valuable. Users will describe it as "I lit a candle for them" or "I added a memory to their room." Success means the action is obvious, low-friction, and emotionally safe—so contributors don't hesitate and organizers see the space come to life.

### 2.2 User Mental Model

- **How users think about it:** "I'm adding my memory to a shared place for [person]," not "I'm posting on a feed." The room is "for" the person; Moments and Tributes are the themed containers; a candle is "my contribution." Contribution is optional and can be short or anonymous.
- **Expectations:** Simple form, no heavy signup, and reassurance that whatever they write is enough. They may compare to signing a condolence book, leaving a note, or sending a card—small, meaningful, not performative.
- **Confusion risks:** Unclear where to start ("Which Moment or Tribute?"), fear their note isn't "enough," or too many steps before submit. Mitigate with one clear CTA, gentle copy, and optional name/guest.

### 2.3 Success Criteria

- **"This just works":** One visible "Light a candle" from room and from each Moment/Tribute; minimal fields (message, then optional name and media); submit and see confirmation without extra steps.
- **Feeling accomplished:** Clear confirmation (e.g. "Thank you. Your candle is now part of this [moment/tribute]") and seeing their candle in the list; no sense they had to "perform."
- **Feedback:** Inline confirmation (in-page, not modal); candle appears in the list (or "pending" if approval is on). Errors (e.g. required field, upload failure) are explained simply and without blame.
- **Speed:** Submit-to-confirmation within a few seconds for text-only; photo upload shows progress and then confirm when done.

### 2.4 Novel UX Patterns

- **Established + ritual frame:** The interaction is a familiar "add a note" form. The novelty is the framing: **Light** + room, Moment/Tribute, candle hierarchy. No new interaction paradigm; optional light education via copy and IA (e.g. "Choose a Moment or Tribute to add your memory").
- **Adopt:** Simple form pattern, optional media, optional name/guest; clear primary button and success state.
- **Unique twist:** Ritual language and single hero CTA; permission-giving copy ("There's no right way… Whatever you share is enough"); optional anonymity so short or hesitant contributions feel valid.

### 2.5 Experience Mechanics

**1. Initiation**

- **Where:** **Light** CTA on the room view (e.g. near list of Moments and Tributes or in a persistent spot) and inside each Moment or Tribute (above or below the candle list).
- **Trigger:** Single primary button or link; label is "Light a candle" (or "Add a memory" as secondary if needed). No competing primary actions on that screen.

**2. Interaction**

- **Flow:** User taps CTA → Moment or Tribute chosen (if from room) or Moment/Tribute is implicit (if already in one) → in-page form expands inline within the Moment/Tribute view: message (required), display name or "Someone" (optional), optional photo or link (URL).
- **Controls:** Text area for message; text field or dropdown for name/Someone; optional upload for photo; optional URL field for link (e.g. video, article). Submit button clearly labeled (e.g. "Light candle" or "Add candle").
- **Response:** On submit, show loading or disabled state; then success path or inline validation/error.

**3. Feedback**

- **Success:** Confirmation message that states the outcome (e.g. "Thank you. Your candle is now part of this [moment/tribute]."). If approval is required: "Your candle has been added and will appear once the room creator approves it."
- **Errors:** Required message missing or upload failed → inline message, no blame; retry or fix and resubmit.

**4. Completion**

- **Done:** User sees confirmation and can navigate back to the Moment or Tribute to see their candle in the spread (their name and message shown like the others). No forced next step; optional "Add another" or return to room or Moment/Tribute.
- **Next:** User can leave, browse other Moments and Tributes, or return later; no gamification or "engagement" prompts.

## Visual Design Foundation

### Color System

- **Direction (Bold & Dignified):** **Chosen palette: A. Slate & silver.** Dark slate header (#2d3748 → #1a202c), soft gray accent (#718096, #4a5568), cool white background (#f7fafc, #fff). Calm, understated, dignified. Alternative options (B–D) remain in `ux-design-directions.html` if revisiting. Backgrounds: cool white or very light gray; avoid warm cream for consistency with chosen palette. No neon or high-saturation "product" primaries. Candle flame stays warm (orange/amber) for "lit" metaphor; wax can be neutral gray to match palette.
- **Semantic mapping:** Primary CTA ("Light a candle") uses warm amber or gold; success/confirmation can use a dignified green or the same warm accent; error and warning remain clear and non-alarming. Candle or flame accents can echo the primary warm tone.
- **Backgrounds and surfaces:** Warm, inviting backgrounds (cream, light warm gray, or very subtle amber wash); cards/surfaces with soft shadow or warm border for depth. Candle imagery (icons, subtle illustrations) can use the same warm accent or a restrained gold/amber.
- **Accessibility:** All text and UI meet WCAG 2.1 AA contrast; bolder colors are chosen so foreground/background ratios remain compliant. Focus and hover states stay visible and dignified.

### Typography System

- **Tone:** Readable, calm, and approachable—neither corporate nor playful. Suited to short copy (room intro, Moment/Tribute titles, candle text) and form labels; support for longer candle text where users write more.
- **Hierarchy:** Clear scale for room name/title, Moment/Tribute titles, body/candle content, and secondary/caption text (e.g. author, date). Sufficient size and line height for body and form fields to reduce cognitive load.
- **Type scale:** Establish a modest scale (e.g. 1.125–1.25 ratio) so hierarchy is clear without dramatic jumps. Body text at least 16px equivalent for readability; touch targets and labels legible on mobile.
- **Accessibility:** Sufficient contrast; avoid very thin or decorative fonts for body; support resizing and screen readers (semantic headings, labels).

### Spacing & Layout Foundation

- **Density:** Generous spacing—airy layout, not dense or busy. Supports emotional safety and reduces visual stress; room and Moment/Tribute content breathe.
- **Spacing scale:** Consistent scale (e.g. 4px or 8px base) for padding, margins, and gaps. Generous padding in cards, forms, and between sections (room header, list of Moments and Tributes, candle list).
- **Grid and structure:** Simple grid for room view (hero with main image, optional details, owner-added photos, list of Moments and Tributes) and Moment/Tribute view (candles spread—each candle one item showing author name, message, and optional photo/video, with pagination/lazy-load). Single-column or limited columns on mobile; room main image and intro as clear "home," Moments and Tributes as list, and within each Moment or Tribute candles displayed individually (name + message + optional media per candle), not aggregated.
- **Touch and targets:** Adequate touch target size (e.g. 44px min) for primary actions and navigation on mobile; comfortable tap areas for **Light** and Moment/Tribute or card entry.

### Accessibility Considerations

- **Contrast:** All text and UI components meet WCAG 2.1 AA contrast requirements; focus and hover states are visible.
- **Keyboard and focus:** Logical focus order; all core flows (room view, Moment/Tribute view, Light (add candle), room creation, moderation) operable by keyboard; focus indicators clear but not harsh.
- **Labels and semantics:** Form inputs and buttons have visible or programmatic labels; headings and landmarks support screen reader navigation; "Light a candle" and other primary actions are clearly announced.
- **Motion and distraction:** No auto-playing motion or flashing; any transitions are subtle and optional (e.g. reduced motion respected). Avoid animations that feel playful or distracting in a memorial context.

## Design Direction Decision

### Design Directions Explored

Five directions were explored in `ux-design-directions.html` (including the chosen Bold & Dignified), with earlier options reviewed in Party Mode:

- **Bold & Dignified (chosen):** Richer color (warm amber, gold, deep neutrals), dignified candle imagery (icon next to Moments and Tributes and in CTAs), confident hierarchy. Lights up emotions while honoring the person remembered; gravitas and warmth together.
- **Calm Minimal:** Maximum white space, subtle gray, minimal accent; quiet and uncluttered. Supports low cognitive load and one clear CTA.
- **Warm Ritual:** Cream and soft amber undertones; gentle warmth without literal "candle" orange. Signals "this is a special place" without branding grief.
- **Soft Editorial:** Clear typographic hierarchy, optional serif for headings; can feel more magazine-like than memorial if overused.
- **Quiet Cards:** Card-heavy layout, soft shadows, rounded corners; risk of feeling product-like rather than a single holding space.

### Chosen Direction

**Bold & Dignified.** A more expressive visual direction that lights up emotions while honoring the dignity of the person remembered: richer color (warm amber, soft gold, deep accents), deliberate use of candle imagery as a respectful ritual symbol, and confident typography and spacing. The look should feel meaningful and memorable without being loud or playful—gravitas and warmth together.

### Design Rationale (Stakeholder + Party Mode)

- **Emotional resonance:** Bolder color and candle imagery help the space feel like a dedicated place of remembrance; they support the ritual of "lighting a candle" and can deepen connection for visitors and organizers.
- **Dignity first:** Candle imagery is used with restraint and respect—e.g. small candle icon or illustration next to Moment/Tribute titles, subtle flame in the hero CTA, or a single dignified candle motif—not decorative or kitsch. Palette remains warm and rich (amber, gold, deep neutrals, optional deep blue or burgundy for gravitas), not bright or gamified.
- **Candles spread, not aggregated:** In Moment/Tribute view, each candle is shown individually (spread): author name (or "Someone") and the message/sentence they wrote. No aggregation that collapses candles into a single count; the Moment or Tribute shows a list of individual candles so visitors see who lit each one and what they said.
- **Hierarchy and clarity:** One hero CTA ("Light a candle") remains; candle visuals reinforce the metaphor rather than compete with it. Reassurance copy and structure stay in place for emotional safety.

### Implementation Approach

- Implement the Bold & Dignified direction using the themeable design system: richer color tokens (warm amber/gold primary, deep accent options, dignified neutrals), confident type scale, generous spacing.
- **Candle imagery:** Include candle visuals in a dignified way—e.g. small candle icon next to each Moment or Tribute in the list, candle or flame accent on or near the primary "Light a candle" button, optional subtle candle illustration in room hero or empty states. Use a consistent, respectful style (e.g. line art or soft illustration); avoid clip-art or cartoonish treatment.
- **Candle display in Moment/Tribute view:** Show candles spread (one per row/card). Each candle displays: (1) an animated candle that looks lit, (2) the name of the person who lit it (or "Someone"), (3) the message or sentence they wrote, (4) optional photo or link attached by the contributor, and (5) a time summary for when the candle was lit ("Lit X years/months/days ago"). Pagination or lazy-load when there are many candles; no aggregation that hides individual contributions.
- Keep "Light a candle" as the single hero CTA; place reassurance copy ("There's no right way…") immediately with the message input. Ensure contrast and accessibility (WCAG 2.1 AA) with the bolder palette.

## User Journey Flows

Critical flows are derived from the PRD: Family Organizer creates room and invites; Contributor visits and lights a candle; Organizer moderates; Contributor (or Organizer) returns. Below are the detailed flows and patterns.

### 1. Family Organizer – Create room and invite

**Goal:** Create a room, add Moments and/or Tributes, get the room URL with "Copy link" and "Copy message" helpers, and share so others can visit and contribute.

**Entry:** Search or word of mouth → land on product → create account (email + name).

**Flow:** Create account → Create room (see Room details below) → Choose or add Moments and/or Tributes (starter suggestions available) → Set visibility (public / link-only) and optional “approve new candles” → Room URL is ready; use “Copy link” and “Copy message” from room settings → Share (email, chat) → Later: see candles from others, re-share link (e.g. around anniversaries).

**Room details (owner, all optional except a way to identify the room):**

- **Main image:** One primary image of the person (hero/main photo for the room).
- **Identifying info (all optional):** First name, last name; date of birth; date of passing. Dates can be entered as **year only**, **month and year**, or **full date**. Place of birth (city / state / country); place of death (city / state / country).
- **Photos and images:** Owner can add additional photos and images to the room (gallery or multiple images beyond the main image).

```mermaid
flowchart LR
  A[Land on product] --> B[Create account]
  B --> C[Create room: main image, optional info, photos]
  C --> D[Add/choose Moments & Tributes]
  D --> E[Set visibility + approval]
  E --> F[Copy link + message from settings]
  F --> G[Share link]
  G --> H[See candles from others]
  H --> I[Re-share when needed]
```

**Success:** Room URL and “Copy message” ready in room settings; minimal steps; first candle from someone else = “space is working.”

**Errors:** Validation on required fields; clear message if room creation fails; option to edit room or Moments/Tributes later.

---

### 2. Contributor – Visit and light a candle

**Goal:** Open the room via link, see who it’s for and the Moments and Tributes, read candles, and add a candle (message + optional name + optional photo or link) with minimal friction.

**Entry:** Tap/open room URL (no account required to view).

**Flow:** Open link → Room view (who it’s for, optional details, main image, list of Moments and Tributes with candle counts) → Open a Moment or Tribute → See candles spread (name + message + “Lit X ago”; candles may include photo or link) → Tap “Light a candle” → In-page form expands: message (required), name or “Someone” (optional), optional **photo or link** attachment → Submit → Confirmation (“Your candle is now part of this [moment/tribute]”) → See their candle in the spread.

**Candle content (contributor):** Text is required. Contributor can optionally attach **one photo and/or one link** (URL to a video, article, or other resource) to their candle (in addition to the message).

```mermaid
flowchart LR
  A[Open room URL] --> B[Room view]
  B --> C[Open Moment or Tribute]
  C --> D[Read candles spread]
  D --> E[Tap Light a candle]
  E --> F[Message + name + optional photo/link]
  F --> G[Submit]
  G --> H[Confirmation]
  H --> I[See candle in list]
```

**Success:** One clear CTA; reassurance copy; minimal fields; immediate confirmation and candle visible in list (with photo or link if attached).

**Errors:** Required message missing → inline validation; submit failure → clear message and retry.

---

### 3. Family Organizer – Moderate (remove candle)

**Goal:** Remove an inappropriate or mistaken candle (or Moment/Tribute) and keep the room safe without support.

**Entry:** Open room (as creator) → Navigate to Moment/Tribute or room view where the candle appears.

**Flow:** View candle → Use “Remove” / “Delete candle” (visible to creator only) → Confirm removal → Candle removed from Moment/Tribute → Optionally re-share room link with a short note.

```mermaid
flowchart LR
  A[Open room as creator] --> B[See candle]
  B --> C[Remove / Delete candle]
  C --> D[Confirm]
  D --> E[Candle removed]
  E --> F[Optional: re-share link]
```

**Success:** Control is obvious but unobtrusive; confirmation avoids accidental delete; no need to contact support.

**Errors:** If remove fails, show clear message and retry.

---

### 4. Contributor – Return visit / lost link

**Goal:** Return to the room (e.g. anniversary) or find it again after losing the link.

**Flow (return):** Same URL (bookmark or saved link) → Room view (unchanged) → Browse Moments and Tributes and candles or light a new candle. No re-onboarding.

**Flow (lost link):** If link-only room, search won’t find it → Get link again from organizer or family → Open link → Same room view as first time; optional gentle cue that the space is still here.

---

### Journey patterns

- **Navigation:** Room → list of Moments and Tributes → Moment or Tribute (candles spread). One level down from room; one level into a Moment or Tribute. “Light a candle” available from room and from within each Moment or Tribute.
- **Decisions:** Organizer: visibility and approval at room creation; Contributor: which Moment or Tribute (if starting from room), name vs “Someone.” No branching that blocks core success.
- **Feedback:** Confirmation after submit (“Your candle is now part of this [moment/tribute]”); candle visible in list; optional “pending” state when approval is on. Errors inline, no blame.

### Flow optimization principles

- **Minimize steps to value:** Contributor: link → room → Moment or Tribute → Light → message → submit → done. Organizer: account → room → Moments/Tributes → copy link → share.
- **One hero CTA per context:** “Light a candle” is the primary action; no competing primary buttons.
- **Reassurance at the right moment:** Permission-giving copy next to the message field; optional name/“Someone” so short or anonymous contributions feel valid.
- **Graceful errors:** Inline validation; clear retry or fix; no dead ends.
- **Return visits:** Same URL; no re-onboarding; optional subtle “still here” cue for anniversaries.


## Component Strategy

### Design System Components (foundation)

Use the themeable design system for:

- **Layout:** Grid, container, spacing scale (Slate & silver tokens).
- **Forms:** Text input, textarea, label, validation message — for room creation (main image, optional details, photos) and "Light a candle."
- **Buttons:** Primary CTA ("Light a candle" / "Light candle"), secondary (e.g. "Cancel"), destructive ("Remove") — all with Slate palette and a11y.
- **Cards / surfaces:** For room card, Moments and Tributes list container, candle row container; borders and shadows from tokens.
- **Focus and keyboard:** Logical order, visible focus, labels — no custom behavior that breaks a11y.

Customize only tokens (color, type, spacing) and any component overrides needed for the chosen palette and tone.

### Custom Components

**1. Room hero / header**

- **Purpose:** Introduce the room: main image of the person, optional details (first/last name, dates of birth and passing, places of birth and death), and owner-added photos. Establishes context for contributors.
- **Content:** Main image; optional first name, last name; date of birth (year only, month+year, or full date); date of passing (same flexibility); place of birth (city/state/country); place of death (city/state/country); gallery or list of additional photos/images. All fields optional.
- **Actions:** None required; optional "Edit" for creator only (navigates to room settings).
- **States:** Default; loading (skeleton) if room data is loading.
- **Accessibility:** Semantic heading, image alt text, sufficient contrast (Slate & silver).

**2. Moment/Tribute list item**

- **Purpose:** One Moment or Tribute in the room: theme name and candle count (or count only), link to open it.
- **Content:** Moment or Tribute title; optional "X candles" or count.
- **Actions:** Tap/click to open Moment or Tribute. Optional candle icon (dignified, from design direction).
- **States:** Default, hover/focus.
- **Accessibility:** Link or button with clear label; count available to screen readers.

**3. Candle row (spread)**

- **Purpose:** One candle in a Moment or Tribute: who lit it, what they wrote, optional photo or link, and when.
- **Content:** Animated lit-candle asset (small), author name (or "Someone"), message text, optional photo or link attachment, "Lit X ago" (years/months/days).
- **Actions:** None for most users; for room creator only, optional "Remove" with confirm.
- **States:** Default; loading (skeleton); optional "pending" when approval is on.
- **Accessibility:** Candle animation optional or reduced for prefers-reduced-motion; name and message in readable order; time summary and media (alt/caption) announced.

**4. Light-a-candle form (in-page)**

- **Purpose:** Collect message (required), display name or "Someone" (optional), optional photo or link; submit to add candle.
- **Presentation:** The form expands **inline within the Moment/Tribute view** (not a modal). This keeps the contributor grounded in the memorial context rather than feeling like they've been pulled into a transactional popup. On mobile, the form slides in below the CTA or at the top of the candle list; on desktop, it can appear in the same column. A "Cancel" or collapse action returns to the candle list without navigating away.
- **Content:** Message textarea with reassurance copy immediately visible (e.g. "There's no right way to do this. Whatever you share is enough."), name input or "Someone" option, optional "Add photo" button, optional link (URL) field (e.g. "Share a link — a video, article, or anything meaningful"), primary submit ("Light candle").
- **Actions:** Submit; cancel/collapse. Optional "Add photo" / "Add link" after message.
- **States:** Default (collapsed / CTA visible), expanded (form visible), loading (submit), validation error (inline), success (confirmation message replaces form, then candle appears in spread).
- **Accessibility:** Labels, error association, focus order, keyboard submit; WCAG 2.1 AA. Focus moves to the message textarea when form expands; focus moves to confirmation or new candle on success.

**5. Share block (organizer, in room settings)**

- **Purpose:** Help the organizer share the room URL. Located in room settings (not a separate system). The room's URL is the permanent, shareable link — no separate invite-link generation.
- **Content:** Room URL displayed with "Copy link" button; pre-written copyable message text (e.g. for email/chat) with "Copy message" button. The message includes the room URL and a brief, warm line (e.g. "I created a space to remember [name]. You can visit and share a memory here: [URL]").
- **Actions:** Copy link, copy message.
- **States:** Default; "Copied" feedback.
- **Accessibility:** Button labels ("Copy link", "Copy message"); feedback announced.

**6. Moderation control (remove candle)**

- **Purpose:** Let room creator remove a candle (or Moment/Tribute) with confirmation.
- **Content:** "Remove" or "Delete candle" (and optional "Delete [moment/tribute]" where applicable).
- **Actions:** Trigger remove → confirm → remove.
- **States:** Default; confirming; loading.
- **Accessibility:** Destructive action clearly labeled; confirmation dialog focus and escape.

### Component Implementation Strategy

- Build custom components on top of design system tokens (Slate & silver) and use foundation components (buttons, inputs, cards) where they fit.
- Keep one hero CTA per view; reuse the same **Light** (or "Light a candle") entry point from room and from each Moment/Tribute.
- Reuse candle row for all candles (spread); animate only the lit-candle asset; support optional photo or link in candle row.
- Room hero supports main image, all optional detail fields (with flexible date and place entry), and owner-added photos/images.
- Ensure all custom components support keyboard and screen readers; test focus order and labels.

### Implementation Roadmap

- **Phase 1 – Core:** Room hero (main image, optional details, owner photos), list of Moments and Tributes, Moment/Tribute view (candles spread), candle row (with optional photo/link), in-page Light form (message + optional photo or link), primary CTA. Required for Organizer create+invite and Contributor visit+Light.
- **Phase 2 – Organizer:** Share block (room URL + copyable message in room settings); room create/edit (main image, optional name/dates/places, Moments and Tributes, visibility, approval, additional photos). Supports full organizer journey.
- **Phase 3 – Moderation and polish:** Remove candle (and optional remove Moment/Tribute); confirmation dialogs; optional "pending" state for candles when approval is on; empty states or loading skeletons.


## UX Consistency Patterns

### Button Hierarchy

- **Primary:** One per view. **Light** (or "Light a candle") is the only primary CTA on room and on each Moment/Tribute; Slate primary (#4a5568 or equivalent). Use for submit on Light-a-candle form.
- **Secondary:** "Cancel", "Close", "Back" — lower emphasis (outline or text), no competition with primary.
- **Destructive:** "Remove" / "Delete candle" (creator only); clearly labeled, with confirmation before action.
- **Touch targets:** Minimum 44px height/width on mobile; adequate spacing between buttons.

### Feedback Patterns

- **Success:** After lighting a candle: short confirmation ("Your candle is now part of this [moment/tribute]"); candle appears in the spread. Optional brief "Copied" for link/message copy actions. No auto-dismiss that's too fast to read.
- **Error:** Inline where possible (e.g. under message field); clear, non-blaming copy; path to fix (e.g. "Add a message").
- **Loading:** Disabled primary button or subtle spinner on submit; for photo upload, progress or "Uploading…" so users know it's in progress.
- **Validation:** Inline on blur or submit; required message on Light-a-candle form; date/place fields follow room optional-field rules.

### Form Patterns

- **Light-a-candle:** In-page form (not modal). Message (required) first; name or "Someone" next; optional photo or link last. Reassurance copy next to message. Single submit; no multi-step wizard.
- **Room create/edit:** Main image; optional fields (first/last name, DOB, date of passing, place of birth, place of death) with flexible inputs (year only, month+year, or full date; city/state/country). All optional. Additional photos/images as gallery or list. Labels and hints clear; no mandatory fields beyond what's needed to create the room.
- **Labels:** Visible and associated (for a11y); placeholder supports but doesn't replace label. Errors associated with inputs.

### Navigation Patterns

- **Room → Moments and Tributes → Moment/Tribute:** One level down into Moments and Tributes; one level into a Moment or Tribute (candles spread). Breadcrumb or back from Moment/Tribute to room when useful; no deep nesting.
- **Persistent CTA:** **Light** available from room view and from within each Moment/Tribute (above or below candle list) so users don't have to go back to find it.
- **No tabs or multi-level nav for MVP:** Flat structure: room, list of Moments and Tributes, Moment or Tribute. Moderation (remove) in context on the candle row for creator.

### Additional Patterns

- **Empty states:** Moment or Tribute with no candles yet: a warm, specific message that acknowledges the courage of going first — e.g. "No one has shared here yet. It can feel hard to go first — but even a few words, or just your name, is a way of saying 'I was here, and I remember.' Whatever you share is enough." Same "Light a candle" CTA follows. Room with no Moments/Tributes: organizer prompt to add Moments or Tributes (if creator).
- **Loading states:** Room and Moment/Tribute use skeleton or minimal spinner; avoid blank screens. Candle row can skeleton while loading.
- **Light-a-candle form:** Always in-page (inline expansion within the Moment/Tribute view), never a modal. This keeps contributors grounded in the memorial context and avoids the frustration of accidental dismissal on mobile. Confirmation appears inline after submit. "Remove candle" confirmation uses a small dialog with clear Confirm/Cancel.
- **Reduced motion:** Respect prefers-reduced-motion for candle flame animation; no essential info in motion alone.


## Responsive Design & Accessibility

### Responsive Strategy

- **Mobile-first:** Primary use is via the room URL on phones. Room view, list of Moments and Tributes, Moment/Tribute view (candles spread), and Light form must work from ~320px up. Single column; room hero (main image + optional details) and Moments and Tributes list stack vertically; candle rows full width; one primary CTA always visible.
- **Tablet:** Same layout as mobile with more comfortable spacing; no separate tablet layout required for MVP. Touch targets and tap areas remain at least 44px.
- **Desktop:** Optional use of max-width container for readability; room and Moment/Tribute content can sit in a centered column. No multi-column candle grid for MVP—candles stay in a single list. Extra space used for padding and breathing room, not extra UI.

### Breakpoint Strategy

- **Base (default):** 320px and up (mobile-first). Single column, stacked sections, full-width CTAs.
- **Breakpoint(s):** Optional at 768px or 1024px to increase max-width of content area and/or padding; no structural change to room → Moments and Tributes → Moment or Tribute. Use relative units (rem, %, min/max-width) so type and spacing scale; avoid fixed px for key layout.
- **Target viewport range:** ~320px to ~1280px (and beyond) without horizontal scroll or clipped content.

### Accessibility Strategy

- **WCAG 2.1 Level AA** for core flows (room view, Moment/Tribute view, Light (add candle), room creation, moderation). Contrast, focus, labels, and keyboard operability per AA.
- **Contrast:** Slate & silver palette chosen so text and UI meet 4.5:1 (normal text) and 3:1 (large text / UI components). Check primary button and links against background.
- **Keyboard:** All primary actions (open Moment or Tribute, Light, submit, copy link, remove candle, confirm/cancel) operable by keyboard; focus order logical; focus visible (clear focus ring).
- **Screen readers:** Semantic structure (headings, landmarks, list for Moments, Tributes, and candles); form labels and errors associated; "Light a candle" and other CTAs announced clearly; candle row content (name, message, "Lit X ago") in readable order. Optional photo: alt text; link: descriptive text.
- **Touch targets:** Minimum 44×44px for primary actions and links on touch devices; adequate spacing between tappable areas.
- **Motion:** Candle flame animation optional or reduced when prefers-reduced-motion is set; no essential information conveyed by motion alone.

### Testing Strategy

- **Responsive:** Test room, list of Moments and Tributes, Moment or Tribute, and Light at 320px, 375px, 768px, 1024px; no horizontal overflow; text readable without zoom.
- **Accessibility:** Run automated a11y checks (e.g. axe, Lighthouse) on key pages; keyboard-only pass through room → Moment/Tribute → Light → submit; test with one screen reader (e.g. VoiceOver or NVDA) for labels, headings, and flow.
- **Real devices:** Spot-check on at least one iOS and one Android device for touch and layout.

### Implementation Guidelines

- **Responsive:** Prefer rem and % for layout and type; use min/max-width and fluid spacing; ensure images (room main image, owner photos, candle photos) scale or constrain so layout doesn't break.
- **Accessibility:** Use semantic HTML (header, main, nav, section, article where appropriate); ensure form inputs have visible labels and error messages linked via aria-describedby or similar; provide skip link(s) if needed for keyboard users; maintain visible focus styles on all interactive elements.
- **Focus:** After submit (light candle), move focus to the confirmation message or the new candle in the spread. After "Remove" confirm, move focus back to the candle list. The Light form is in-page (not modal), so no focus-trap is needed for it; "Remove candle" confirmation dialog traps focus and returns focus on close.
