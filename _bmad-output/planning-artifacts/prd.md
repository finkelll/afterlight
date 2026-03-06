---
stepsCompleted: ['step-01-init', 'step-02-discovery', 'step-02b-vision', 'step-02c-executive-summary', 'step-03-success', 'step-04-journeys', 'step-05-domain', 'step-06-innovation', 'step-07-project-type', 'step-08-scoping', 'step-09-functional', 'step-10-nonfunctional', 'step-11-polish', 'step-12-complete']
inputDocuments:
  - _bmad-output/planning-artifacts/product-brief-ai-2026-03-01.md
  - _bmad-output/planning-artifacts/research/technical-architecture-and-stack-for-afterlight-research-2026-03-01.md
  - _bmad-output/planning-artifacts/research/market-virtual-memorial-platforms-and-online-remembrance-products-like-afterlight-research-2026-03-01.md
workflowType: prd
classification:
  projectType: web_app
  domain: consumer_remembrance
  complexity: medium
  projectContext: greenfield
  domainAlias: grief tech / digital legacy
  primaryDesignDriver: emotional safety and clarity
vision:
  oneSentenceValue: "A shared home for memories where people can visit, share stories, and light a candle, and it will light forever."
---

# Product Requirements Document - Afterlight

**Author:** Finkel
**Date:** 2026-03-01

## Executive Summary

Afterlight is a consumer web app in the grief tech / digital legacy space: a shared memorial experience where families and friends create **rooms** for someone who has died and contribute **candles** (text, photos, or links) inside **Moments** (memories/moments with that person) or **Tributes** (dedications—e.g. song, flower, candle, prayer). The primary user is the Family Organizer who creates the room and shares an invite link; the secondary but critical user is the Contributor who visits via link to read, share a memory, or **light** a candle.

The product's core insight is that people don't need another static tribute page or a noisy social-media feed; they need a calm, emotionally safe "home for memories" that supports ongoing shared remembrance over time. The differentiator is a ritual-like UX (Room → Moments and Tributes → Candles) combined with privacy-first defaults and minimal friction for contribution. The desired "aha" moment is when the organizer sees the first non-creator candle appear and realizes the space is working as a shared home.

### Product terminology

| Concept | Term | Definition |
|--------|------|------------|
| Main space | **Room** | The whole memorial for one person who has died. One room per person. |
| Container type 1 | **Moment** | A place for **sharing a memory or a moment** you had with that person. Focus: personal recollection, story, or shared experience (e.g. "Her laugh," "Stories we tell"). Candles here = "I remember…" / "A moment we shared." |
| Container type 2 | **Tribute** | A place for **dedicating something to or for** that person. Focus: offering, dedication, or gift in their honor—e.g. a song, a flower, a candle (ritual), a prayer, or a **link** (video, article, etc.). Candles here = "This is for you" / "I'm dedicating this to them." |
| Single contribution | **Candle** | One person's contribution inside a Moment or Tribute: text (required) + optional photo or **link** (URL to a video, article, or other resource). |
| Primary action | **Light** | Main CTA (e.g. button "Light"); longer copy: "Light a candle" or "Add your light." |

**Moment vs Tribute:** **Moment** = sharing a memory or moment *with* them (story, experience). **Tribute** = dedicating something *to* them (song, flower, prayer, or shared link e.g. video). The distinction is **organizer-facing scaffolding**: it helps the organizer set up a meaningful structure when creating the room (choosing themes like "Her laugh" vs "A song for her"). For **contributors, the distinction is low-stakes** — any candle in any container is welcome and valid. If a contributor places a dedication inside a Moment or a memory inside a Tribute, that's fine; the system does not enforce or correct this. Copy and prompts lean into this: "Share whatever feels right."

One-sentence value: "A shared home for memories where people can visit, share stories, and light a candle, and it will light forever."

### What Makes This Special

- **Ritual-shaped interaction model:** Rooms, Moments, Tributes, and candles make sharing feel meaningful and structured, not like a comment feed.
- **Emotional safety as a design driver:** Tone, pacing, and UX minimize cognitive load during grief; contributions can be short and still feel valid.
- **Privacy-first, non-exploitative stance:** Link-only visibility for MVP, clear control over who can see/contribute, no ads, no selling or training on user memories.
- **Organizer-friendly onboarding:** Fast setup, starter Moments and Tributes, and a clean room URL with copy helpers make it easy for one person to create value for many.
- **Built for long-tail return visits:** Designed for anniversaries and revisits, not only the immediate days after death.

## Project Classification

- **Project Type:** Web app
- **Domain:** Consumer remembrance (alias: grief tech / digital legacy)
- **Complexity:** Medium (sensitive content, privacy, emotional UX; no heavy regulatory regime assumed)
- **Project Context:** Greenfield
- **Primary Design Driver:** Emotional safety and clarity

## Success Criteria

### User Success

- Organizer creates a room and gets an invite link with minimal friction.
- At least one other person visits via link and lights a candle or leaves a memory (text, and optionally photo or link).
- Contributors can return later (e.g. anniversaries) and the space still feels available and safe.
- "Aha" moment: organizer sees the first candle from someone else and feels the space is working.

### Business Success

- **3–6 months:** Validate that the product creates value—rooms created, candles per room, share of rooms with 2+ contributors; no revenue requirement yet; focus on retention and word-of-mouth.
- **6–12 months:** If validation holds, consider a sustainable model (e.g. optional paid tier) and measure adoption in the chosen region (e.g. North America).

### Technical Success

- No critical reliability or privacy incidents; platform feels safe and stable for sensitive content.
- HTTPS everywhere; data at rest encrypted via managed provider; room and candle data only accessible to those with the link or explicit access.

### Measurable Outcomes

- Rooms created (per week/month).
- Candles per room (median and distribution).
- % of rooms with 2+ contributors.
- Return visits (sessions per room after 7 days, 30 days).
- **Light** (add candle) completion rate (among visitors who start the flow).

### Qualitative Validation

- **Post-contribution pulse:** After a contributor lights a candle and sees the confirmation, offer an optional, single-question prompt (e.g. "Did this feel right?" with simple yes/not-really response). Non-intrusive; dismissed with a tap; never repeated in the same session. Track sentiment ratio over time.
- **Organizer check-in:** After the first non-creator candle appears, prompt the organizer once (e.g. "How is the space feeling so far?") with a simple free-text or emoji-scale response. Use responses to detect early friction or satisfaction.
- **Periodic lightweight interviews:** At 30-day and 90-day marks, invite a small sample of organizers for a brief (10-minute) conversation or async survey focused on: whether the space feels like a "shared home," what prompted return visits, and any unmet needs.
- **Session replay and flow observation:** Use anonymized session recordings (with consent) on core flows (room creation, Light a candle) to identify hesitation, abandonment, or confusion points that quantitative metrics alone won't surface.

## Product Scope

### MVP – Minimum Viable Product

- Rooms (create, view, edit; visibility: **public** or **link-only** at owner’s choice; owner can require **approval for new candles** before they appear).
- **Moments and Tributes** (create, list, view; two container types—Moment = memory/moment with that person, Tribute = dedication e.g. song, flower, candle, prayer; starter suggestions at room creation).
- **Candles** (text required; optional photo or **link**; display; author and room owner can edit/delete).
- Lightweight auth; named or guest contribution via invite link.
- Room URL as the shareable link, with "Copy link" and "Copy message" helpers in room settings.
- Room creator can remove candles or Moments/Tributes; basic spam/abuse handling.
- Grief-sensitive copy and tone; soft, non-gamified UI; mobile-friendly; pagination/lazy-load for candles.

### Growth Features (Post-MVP)

- Optional paid tier for long-term hosting or premium features.
- Deeper support for community/group organizers (e.g. nonprofits, workplaces).
- Optional integrations (e.g. QR or links from physical memorials, anniversary/reminder nudges).

### Vision (Future)

- Broader regional rollout; expansion to additional segments or use cases if validated.

## User Journeys

### 1. Family Organizer – Success path (Maya)

Maya’s mother died two weeks ago. She’s coordinating with siblings and cousins in other cities and wants one place where everyone can share stories and see each other’s words without juggling social media or a sketchy “forever” site.

- **Opening:** She searches for something like “online memorial for family,” finds Afterlight, and lands on the product. She’s tired and skeptical that anything will be simple or lasting.
- **Rising action:** She creates an account (email + name), then a room: her mother’s name, a short line about her, and a photo. She picks a few starter Moments and/or Tributes (“Her laugh,” “What she taught us,” “Stories we tell”). The room is created with a clean URL. She uses “Copy link” and “Copy message” from room settings to send it by email and in the family group chat.
- **Climax:** Within a few days she sees candles from her sister, a cousin, and an old friend. She reads their memories and lights a candle of her own in “Her laugh.” She feels the space is “working” and that her mom is being remembered together.
- **Resolution:** She keeps the link; people add candles over time. She re-shares the link around her mother’s birthday and feels the memorial is a lasting, shared home rather than a one-off page.

### 2. Contributor – Success path (James)

James is a family friend. He gets the invite link from Maya and wants to leave something short and honest without signing up for another platform.

- **Opening:** He taps the link on his phone. He sees who the room is for, a short line, and a list of Moments and Tributes with candle counts. He’s not sure what to write or if his note is “enough.”
- **Rising action:** He opens “Stories we tell,” reads a few candles, and taps “Light a candle.” He sees gentle copy (“There’s no right way… Whatever you share is enough”) and a simple text box. He writes a few sentences and submits. He’s asked for a name (or can stay “Someone”); he adds his name.
- **Climax:** His candle appears right away with a brief “Thank you. Your candle is now part of this [moment/tribute].” He scrolls and sees his note among others. He feels he’s done something meaningful without it being a big production.
- **Resolution:** He bookmarks the room and thinks he might return on an anniversary or when he’s thinking of her.

### 3. Family Organizer – Edge case (re-share and moderation)

Maya notices a candle that’s off-topic or spammy and wants to remove it and keep the room safe without calling support.

- **Opening:** She opens the room and sees a candle that doesn’t belong (spam or mistaken post). She worries the space no longer feels respectful.
- **Rising action:** As room creator she has a “Remove” or “Delete candle” option on that candle. She uses it and confirms. The candle is removed. She can optionally re-share the invite link with a short note (“Link still works; please only share with people who knew Mom”).
- **Climax:** The inappropriate content is gone; she feels she can keep the memorial safe and under her control.
- **Resolution:** She knows she can remove candles or Moments/Tributes if needed and that the room stays link-only, so she keeps using and sharing it.

### 4. Contributor – Edge case (lost link / first-time visitor)

A relative never saved the link and doesn’t know where to go.

- **Opening:** They remember “Maya set up something online for Mom” but don’t have the link. They search for “[Mom’s name] memorial” or ask Maya for the link again.
- **Rising action:** If the room is link-only, search won’t show it; they get the link from Maya (or family) and open it. They land on the same room intro and list of Moments and Tributes as James. If they’re nervous, the **Light** flow and short reassurance copy help them contribute.
- **Climax:** They add a candle and see it appear. They feel included in the shared remembrance.
- **Resolution:** They save or bookmark the link so they can return later.

### Journey Requirements Summary

- **Room creation:** Account/session, create room (name, short description, photo), choose/create Moments and Tributes, set visibility (public or link-only), set whether new candles need owner approval. The room URL is the shareable link; room settings include "Copy link" and "Copy message" helpers for easy sharing.
- **Room view (contributor):** Open via link or (if room is public) via listing/search; see room intro and list of Moments and Tributes.
- **Moment/Tribute view:** List candles, pagination/lazy-load, **Light** entry point.
- **Light (add candle):** Gentle copy, text + optional photo or link, name or “Someone,” submit, confirmation and in-list display.
- **Moderation:** Room creator can delete candle or Moment/Tribute; optional approval queue for new candles when owner enables “approve before visible”; basic spam/abuse handling (e.g. block by email).
- **Re-share:** Same room URL; organizer can use "Copy link" or "Copy message" from room settings anytime to re-send.

## Domain-Specific Requirements

### Visibility & access

- Owner chooses room visibility: **public** (discoverable/listable) or **link-only** (only people with the link can find and open the room).
- Owner can set whether new candles need **approval** before they appear (moderation gate) or go live immediately.

### Privacy & data handling

- No ads; no selling or licensing of user content; no use of memorial content for AI training or marketing.
- If EU users are served later: support data export and account/memorial deletion in line with GDPR-style expectations.

### Emotional safety

- Copy and UX are grief-sensitive: calm tone, no pressure, no gamification (no counts, streaks, or “engagement” prompts).
- “Light a candle” and related flows make it clear that short or anonymous contributions are valid.

### Technical constraints

- HTTPS only; storage and DB via a managed provider with encryption at rest.
- Access control so only the room creator (and any designated moderators) can remove candles or Moments/Tributes or approve pending candles.

### Risks and mitigations

- **Risk:** Sensitive content exposed (e.g. link leaked). **Mitigation:** Link-only by default; owner can switch to approval-required for new candles so unwanted contributions don't appear without review. Future consideration: option to regenerate the room slug (with clear warning that old links will break).
- **Risk:** Platform shutdown or change. **Mitigation:** Clear retention/backup and export (e.g. export room + candles) so families can keep their data.

## Innovation & Novel Patterns

### Detected Innovation Areas

- **Ritual-shaped interaction model (New interaction):** Room → Moments and Tributes → Candles is a deliberate, non-feed pattern. It reframes contribution as “lighting a candle” and groups memories by theme (Moments = memories/moments, Tributes = dedications), avoiding comment-thread noise and one-off tribute walls. This is a novel interaction pattern in the grief-tech / memorial space.
- **Emotional safety as a primary design driver:** Explicit design goal to minimize cognitive load and pressure during grief; short or anonymous contributions are first-class. Most memorial products optimize for engagement or permanence claims rather than calibrated emotional safety.
- **Privacy-first, non-exploitative stance:** No ads, no selling or licensing of content, no AI training on memories. Link-only and approval gates put control with the family. Differentiates from ad-supported or data-monetized alternatives.
- **Organizer-led, low-friction shared space:** One person creates value for many via a single invite link and copyable message; starter Moments and Tributes reduce setup friction. Aligns with “Family Organizer” as primary user and validates shared adoption.

### Market Context & Competitive Landscape

- Incumbents: Funeral-home obituary pages, legacy “forever” memorial sites, and social-media tributes. Pain points include static one-way pages, reliability/uptime issues, opacity on permanence, and weak support.
- Unmet needs: Assured long-term stewardship, more interactive and conversational spaces, clear privacy/ownership, and experiences that feel like a continuing conversation rather than a one-time post.
- Afterlight’s position: Combines ritual-like structure (Room → Moments and Tributes → Candles), emotional-safety-first UX, and clear privacy/export promises to address permanence anxiety and desire for living, shared remembrance.

### Validation Approach

- **Quantitative (3–6 months):** Rooms created, candles per room, % rooms with 2+ contributors, return visits (7-day, 30-day), and “light a candle” completion rate.
- **Qualitative (ongoing):** Post-contribution pulse (“Did this feel right?”), organizer check-in after first non-creator candle, periodic lightweight interviews at 30/90 days, and anonymized session replay on core flows. See “Qualitative Validation” under Success Criteria for details.
- **Innovation validation:** Ritual model works if median candles per room and share of rooms with multiple contributors meet targets; emotional safety reflected in low abandonment in “Light a candle” flow, positive pulse responses, and organizer check-in sentiment.
- **Fallback:** If ritual structure underperforms, retain core value (privacy, export, calm UX) and iterate on Moment/Tribute/candle framing or onboarding based on usage and qualitative feedback. The Moment vs. Tribute distinction is organizer-facing scaffolding and low-stakes for contributors; if user testing shows the distinction causes confusion, it can be simplified to a single container type without breaking the core model.

### Risk Mitigation

- **Innovation risk:** Ritual metaphor may not resonate for all segments. Mitigation: Keep copy inclusive; support both “light a candle” and plain “add a memory” mental models where appropriate; test with diverse organizers and contributors.
- **Market risk:** Incumbents or new entrants copy the pattern. Mitigation: Lead on trust, privacy, and emotional safety; strong execution on reliability and support; optional paid tier and clear long-term value for retention.

## Web App Specific Requirements

### Project-Type Overview

Afterlight is a consumer web application used in-browser on desktop and mobile. Primary access is via invite links; discovery may include search when rooms are public. SPA or MPA is an implementation choice; the product must feel fast and calm, with no heavy real-time requirements for MVP beyond loading and submitting candles.

### Technical Architecture Considerations

- **Browser support:** Support current versions of Chrome, Safari, Firefox, and Edge on desktop and mobile. No requirement for legacy browsers (e.g. IE11).
- **Responsive design:** All core flows (room view, Moment/Tribute view, Light (add candle), room creation, moderation) must be usable on viewports from ~320px (phone) to desktop. Touch targets and reading comfort matter for grief-sensitive use on phones.
- **Performance:** Room and Moment/Tribute views should load quickly so visitors are not left waiting on a blank or spinning screen. Pagination or lazy-load for candles keeps initial load bounded. No specific real-time push for MVP.
- **SEO:** For link-only rooms, SEO is irrelevant (no indexation). For public rooms, room title and short description should be indexable so that search for the person’s name can surface the memorial; no requirement for deep Moment/Tribute/candle indexing in MVP.
- **Accessibility:** Align with WCAG 2.1 Level AA where applicable (keyboard navigation, focus order, labels, contrast, readable text). Emotional-safety and inclusive design extend to users with varying abilities; forms and “Light a candle” must be usable with screen readers and without a mouse.

### Implementation Considerations

- **Authentication:** Lightweight auth (e.g. email-based) for room creators; contributors may use name-only or guest flows via invite link. No mandatory social login for MVP.
- **Offline:** No offline-first requirement for MVP; the app assumes connectivity. Optional future: basic offline readability or queue for candle submission.
- **Progressive enhancement:** Core flows must work without JavaScript where feasible (e.g. submit candle, view room) or degrade gracefully; primary experience can assume JS for interactivity and pagination.

## Project Scoping & Phased Development

### MVP Strategy & Philosophy

**MVP Approach:** Problem-solving MVP—deliver the minimum that makes organizers and contributors say "this is useful": one person can create a room, share a link, and at least one other person can visit and light a candle or leave a memory. Fast path to validated learning: rooms created, candles per room, % rooms with 2+ contributors.

**Resource assumptions:** Small team; scope bounded to rooms, Moments and Tributes, candles, invite link, lightweight auth, and moderation. No paid tier or advanced integrations in MVP.

### MVP Feature Set (Phase 1)

**Core user journeys supported:** Family Organizer creates room and invites others; Contributor visits via link and lights a candle or leaves a memory; Organizer moderates (remove candle or Moment/Tribute, optional approval queue); Contributor or Organizer re-visits (e.g. anniversary).

**Must-have capabilities:** Room CRUD with visibility (public/link-only) and optional approval for new candles; Moments and Tributes (create, list, view; two container types) with starter suggestions; candles (text required, optional photo or link, display, edit/delete by author or owner); room URL as the shareable link (no separate invite-link system — the room's URL is what the organizer shares, with a "Copy link" and optional "Copy message" helper in room settings); lightweight auth for creator; named or guest contribution via link; grief-sensitive copy and tone; mobile-friendly layout; pagination/lazy-load for candles; room creator can remove candles or Moments/Tributes and basic spam/abuse handling.

### Post-MVP Features

**Phase 2 (Growth):** Optional paid tier for long-term hosting or premium features; deeper support for community/group organizers (e.g. nonprofits, workplaces); optional integrations (e.g. QR or links from physical memorials, anniversary/reminder nudges).

**Phase 3 (Expansion):** Broader regional rollout; additional segments or use cases if validated.

### Risk Mitigation Strategy

**Technical:** Most complex areas are photo upload and approval workflow; mitigate with simple upload and a clear pending/approved state. **Market:** Validate with rooms created and multi-contributor share before monetization. **Resource:** MVP is shippable with a small team; defer paid tier and integrations to Phase 2.

## Functional Requirements

### Room Management

- FR1: Room creator can create a room with name, short description, and photo.
- FR2: Room creator can set room visibility to public (discoverable/listable) or link-only.
- FR3: Room creator can set whether new candles require owner approval before they appear.
- FR4: Room creator can view and edit room details (name, description, photo, visibility, approval setting).
- FR5: Room creator can delete the room (with appropriate confirmation and data-handling).
- FR6: Visitor with the room link (or discoverer for public rooms) can view the room intro, description, photo, and list of Moments and Tributes.

### Moments and Tributes (container types)

- FR7: Room creator can create Moments and Tributes (with title or theme). Moment = container for memories/moments with that person; Tribute = container for dedications (e.g. song, flower, candle, prayer).
- FR8: Room creator can choose from starter Moment and Tribute suggestions when creating a room.
- FR9: Room creator can list, view, and delete Moments and Tributes.
- FR10: Visitor can view the list of Moments and Tributes for a room with candle counts (or equivalent indicator).
- FR11: Visitor can open a Moment or Tribute and see its candles (with pagination or lazy-load).

### Candles (Memories)

- FR12: Visitor with room access can add a candle to a Moment or Tribute (text required; optional photo and/or link).
- FR13: Visitor can provide a display name or contribute as "Someone" (or equivalent anonymous option).
- FR14: System displays candles in the Moment or Tribute with author attribution (name or anonymous) and content.
- FR15: Candle author can edit or delete their own candle.
- FR16: Room creator can edit or delete any candle in the room.
- FR17: When approval is required, room creator can approve or reject pending candles; approved candles then appear in the Moment or Tribute.

### Sharing & Access

- FR18: The room's URL is the shareable link. Room settings include a "Copy link" button and a "Copy message" helper (pre-written text the organizer can paste into email, chat, etc.). No separate invite-link generation system — the room URL is stable and permanent.
- FR19: Anyone with the room URL can open the room (subject to visibility) and view Moments, Tributes, and candles.
- FR20: Room creator can use "Copy link" or "Copy message" from room settings at any time to re-share.
- FR21: For link-only rooms, only users with the URL can find and open the room (no public listing or search). The URL is not guessable (e.g. uses a random slug or UUID).

### Authentication & Identity

- FR22: Room creator can create an account (e.g. email and name) to create and manage rooms.
- FR23: Contributor can add a candle with a display name or as guest/"Someone" without creating an account (when allowed by room).

### Moderation & Safety

- FR24: Room creator can remove (delete) any candle in the room.
- FR25: Room creator can remove (delete) any Moment or Tribute in the room.
- FR26: System supports basic spam/abuse handling (e.g. block by email or similar) as specified in domain requirements.

### Content & Media

- FR27: Candles can include text (required), optional photo, and optional link (URL to a video, article, or other resource).
- FR28: Room supports a primary photo for the room (e.g. of the person being remembered).
- FR29: Room and candle content are displayed in a grief-sensitive, calm manner (tone and presentation per domain requirements).

### Export & Stewardship

- FR30: Room creator can export the full room as a downloadable archive. The export includes:
  - A **readable PDF** of the room: room details (name, description, dates, places, main image), each Moment and Tribute with its candles (author, message, timestamp), and any attached photos rendered inline. This is the "keepsake" format families can print or share.
  - A **structured JSON file** containing all room data, Moment/Tribute metadata, and candle records (text, author, timestamps, photo URLs, link URLs) for portability and re-import.
  - A **media folder** with all uploaded photos at original resolution.
  - The archive is delivered as a single `.zip` file. Export is available from room settings for the room creator at any time. The system should complete export within a reasonable time (target: under 60 seconds for rooms with up to 500 candles and associated photos).

## Non-Functional Requirements

### Performance

- NFR1: Room and Moments/Tributes listing pages load and render key content within 3 seconds under normal load (95th percentile), as measured by real-user or synthetic monitoring.
- NFR2: Submission of a candle (text-only) completes and confirms to the user within 5 seconds under normal conditions; photo upload may have longer acceptable latency with clear progress indication.
- NFR3: Pagination or lazy-load keeps initial page payload bounded so that rooms with many candles do not block initial render.

### Security

- NFR4: All access to the application is over HTTPS only; no mixed content or downgrade.
- NFR5: Room and candle data are stored with encryption at rest via the chosen managed provider.
- NFR6: Access control enforces that only the room creator (and any designated moderators) can remove candles or Moments/Tributes or approve pending candles; only holders of the invite link (or public discovery for public rooms) can view and contribute as defined.
- NFR7: No advertising; no selling or licensing of user content; no use of memorial content for AI training or marketing (per domain requirements).

### Reliability & Availability

- NFR8: The application is available for read and write operations with target uptime consistent with a consumer web app (e.g. 99.5% or better during core hours), as measured by the hosting/monitoring stack; planned maintenance may be excluded with notice.
- NFR9: Data durability and backup practices ensure room and candle data can be recovered in line with provider and product commitments; export supports family stewardship (per domain/risk mitigations).

### Accessibility

- NFR10: The application meets WCAG 2.1 Level AA for core flows (room view, Moment/Tribute view, Light (add candle), room creation, moderation) where applicable—keyboard navigation, focus order, labels, contrast, and readable text—as verified by review or testing.
- NFR11: The **Light** flow and other contribution flows are usable with screen readers and without mouse dependency, in line with emotional-safety and inclusive design goals.
