stepsCompleted: [1, 2, 3, 4, 5, 6]
inputDocuments: [
  "_bmad-output/planning-artifacts/research/technical-architecture-and-stack-for-afterlight-research-2026-03-01.md",
  "_bmad-output/planning-artifacts/research/market-virtual-memorial-platforms-and-online-remembrance-products-like-afterlight-research-2026-03-01.md"
]
date: 2026-03-01
author: Finkel
---

# Product Brief: Afterlight

<!-- Content will be appended sequentially through collaborative workflow steps -->

---
## Executive Summary

**Afterlight** is a gentle, private web app where families and friends create shared memorial spaces (“rooms”) for someone who has died. People add memories as “candles” (text, photos, or voice) inside themed threads, invite others via a link, and return over time. Success means seeing others visit, share memories, or simply light a candle—creating real value for people in grief. The product differentiates on **trust and permanence**, **simple ritual-like UX** (rooms, threads, candles), and **no ads or AI gimmicks**, filling a gap left by static tribute pages, fragile legacy platforms, and social media.

---
## Core Vision

### Problem Statement

Families and friends lack a **simple, trustworthy place** to remember someone together online—one that feels **lasting**, **respectful**, and built for **shared stories and small gestures** (like lighting a candle) instead of static pages, ads, or gimmicks.

### Problem Impact

When this need goes unmet, organizers juggle funeral-home sites, social posts, and third-party memorial tools that often feel unreliable, opaque, or emotionally mismatched. Contributors hesitate to share; pages go stale; people worry their tributes will vanish if a platform shuts down. Grief is compounded by technical anxiety and a sense that nothing “good enough” exists.

### Why Existing Solutions Fall Short

- **Static tribute / obituary pages**: Become “digital ghost towns”; one-way posting, no sense of ongoing conversation or living space.
- **Legacy memorial platforms**: History of outages, broken media, poor support, and “forever” promises that aren’t backed by clear policies or export options.
- **Social media**: Algorithms, ads, and noise feel wrong for grief; limited control over who sees what and how long it stays.
- **AI avatar / chatbot memorials**: Novel but raise privacy and “uncanny” concerns; often complex and not the first thing grieving families want.

### Proposed Solution

A **shared home for memories**: private rooms per person, with threads (e.g. “Her laugh”, “Road trips”) and candles (text, photo, or voice). One person creates the room and invites others via link; everyone can light candles and browse in a calm, ritual-like flow. The product is web-first, mobile-friendly, and built to feel safe and enduring—with clear promises about data, backups, and no ads.

### Key Differentiators

- **Trust and permanence**: Plain-language hosting and retention, export/backup options, no dark “forever” upsells.
- **Living space, not a static page**: Threads and candles that grow over time; gentle, grief-sensitive UX.
- **Privacy-first, no exploitation**: No ads, no selling or training AI on memories; control over who can see and contribute.
- **Organizer-friendly**: Fast setup, easy invite link, so the “family organizer” can create value for others without technical burden.

---
## Target Users

### Primary Users

**1. The Family Organizer (room creator)**  
Typically the person who arranges things after a death—often a woman 45–70, but not exclusively. She wants one calm, lasting place where scattered family and friends can share stories and small gestures without juggling funeral-home pages, social posts, or sketchy "forever" sites. She's motivated by making sure the person is remembered well and that others feel invited to contribute. Success for her: creating the room, sending the link, and then seeing others visit, share memories, or light a candle. She needs minimal setup, a clear invite flow, and confidence the space will still be there in years.

**2. The Contributor (friend or relative)**  
Anyone who was close to the person and is invited via link—often 20s–60s, comfortable on phone or laptop. They don't want to manage a memorial; they want to read, maybe leave a short message or a photo, or light a candle when it feels right. Success for them: a simple, respectful place where their contribution feels welcome and they can return on anniversaries or when they're thinking of the person. They need low friction (no heavy signup or complex UI) and reassurance that even a short note is enough.

### Secondary Users

**3. Community or group organizer**  
Clergy, community leaders, nonprofits, or workplace contacts who want to offer a shared space to remember someone (e.g. after a community loss or a colleague's death). They create a room and share the link with a broader group. They benefit from the same core product; v1 can support them with flexible room and invite settings. Deeper B2B/group features can come later.

### User Journey

- **Discovery:** Organizer finds Afterlight via search, word of mouth, or a recommendation when looking for "a place to remember [name] together" or "online memorial without ads." Contributors arrive almost always via the organizer's invite link (email, message, or obituary).
- **Onboarding:** Organizer creates a room (name, short description, optional photo), picks or adds a few starter threads, and gets an invite link. Contributors land on the room, see who it's for and a short line about sharing memories, then either browse or go straight to "Light a candle."
- **Core usage:** Organizer checks in occasionally, adds or curates threads, re-shares the link around anniversaries. Contributors read candles, add their own (text, photo, or voice), and sometimes return on meaningful dates.
- **Success moment:** Organizer sees the first candles from others and feels that the space is "working"; contributors feel they've done something meaningful without it being heavy or public.
- **Long-term:** The room stays available; people drop in when they need to, add a candle or re-read; the space feels like a lasting home for memories rather than a one-time tribute page.

---
## Success Metrics

**User success**  
We're succeeding for users when: (1) organizers create a room and send the link with minimal friction; (2) at least one other person visits and lights a candle or leaves a memory; (3) people can return later (e.g. anniversaries) and the space still feels safe and available. Leading indicators: room creation completed, invite link generated, first candle from someone other than the creator, and repeat visits to the same room over time.

**Business objectives (initial go-to-market)**  
- **3–6 months:** Validate that the product creates value—rooms created, candles per room, share of rooms with multiple contributors. No requirement yet for revenue; focus on retention and word-of-mouth.  
- **6–12 months:** If validation holds, consider a sustainable model (e.g. optional paid tier for long-term hosting or extra features) and measure adoption in the chosen region (e.g. North America).

**Key performance indicators**  
- **Rooms created** (per week/month)—organizer adoption.  
- **Candles per room** (median and distribution)—depth of use and whether others are participating.  
- **% of rooms with 2+ contributors**—whether the “shared home” promise is real.  
- **Return visits** (sessions per room after 7 days, 30 days)—whether the space is used over time, not just at creation.  
- **Light a candle completion rate** (among visitors who start the flow)—usability and emotional fit of the core action.

These metrics tie directly to the vision: creating value for grieving people and “seeing others visit, share memories, or just light a candle.”

---
## MVP Scope

### Core Features

- **Rooms:** Create a room (name, short description, hero photo), view and edit basics. Visibility: link-only (not indexed, no public directory).
- **Threads:** Create thread, list threads in a room, view thread. Starter thread suggestions when creating a room (e.g. "Her laugh", "What they taught us", custom).
- **Candles:** Create candle—text required; optional photo upload, optional audio. Display candles (author, time, content). Author and room owner can edit/delete.
- **Auth / identity:** Lightweight accounts (e.g. email + name). Support named or guest contributions via invite link as appropriate for v1.
- **Invites:** Per-room shareable link; copyable invite message text.
- **Moderation:** Room creator can remove candles or threads; basic spam/abuse handling (delete, block by email).
- **UX:** Grief-sensitive copy and tone; soft, non-gamified UI; mobile-friendly; pagination/lazy-load for candles in a thread.

### Out of Scope for MVP

- Public directories or search across rooms.
- Advanced customization (themes, custom domains).
- AI summarization or auto-generated tributes.
- Complex roles/permissions beyond room owner and contributors.
- Native mobile apps (web only for v1).

### MVP Success Criteria

- Organizers can create a room and get an invite link with minimal friction.
- At least one other person can visit via link and light a candle (text, and optionally photo or voice).
- Core metrics (rooms created, candles per room, % rooms with 2+ contributors, return visits, "light a candle" completion rate) are measurable and show early signs of value.
- No critical reliability or privacy incidents; platform feels safe and stable for sensitive content.

Decision to scale beyond MVP: sustained evidence that rooms are shared, others contribute, and people return over time, plus positive qualitative feedback.

### Future Vision

- Optional paid tier for long-term hosting guarantees or premium features; sustainable business model.
- Deeper support for community/group organizers (e.g. nonprofits, workplaces); B2B/group features.
- Optional integrations (e.g. QR or links from physical memorials, anniversaries/reminders).
- Broader regional rollout and, if validated, expansion to additional segments or use cases.
