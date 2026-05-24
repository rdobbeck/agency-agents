# Client Acquisition Engine — Personal Training

A repeatable, multi-agent marketing system for filling 1:1 slots, remote
coaching, cohorts, and small-group classes. Built on the agents in this repo and
run as a monthly loop so results compound.

**Goal:** turn attention into booked consults into paying clients, on a schedule
you can repeat every month.

---

## How to use this

1. Fill in `inputs.md` once (your offers, ICP, location, platforms, prices).
2. Run the four stages below in order. Each stage has a copy-paste prompt that
   activates the right agent(s) and feeds them your inputs.
3. Save each stage's output back into this folder (filenames suggested below).
4. Re-run Stage 2 (content) every month, Stages 1/3 quarterly, and review the
   KPI tracker weekly.

Run it agent-by-agent, or run the whole thing with the **Orchestrator prompt**
at the bottom (NEXUS-Micro mode).

---

## Stage 1 — Positioning (do once, revisit quarterly)

**Agents:** Trend Researcher, Brand Guardian
**Output:** `01-positioning.md` (ICP, offer ladder, 3-5 message pillars)

```
Activate Trend Researcher, then Brand Guardian.

My business: [paste inputs.md]

Trend Researcher: scan my local + online market. Who are my competitors, what
are they charging, what demand signals and underserved segments exist for my
niche? Give me 3 positioning angles I can own.

Brand Guardian: using the best angle, produce:
- A one-sentence positioning statement ("I help [who] achieve [outcome] through [how]")
- My Ideal Client Profile (demographics, goals, pains, objections, where they hang out)
- An offer ladder: free lead magnet -> low-ticket (small group/cohort) -> core (1:1 / remote) -> premium
- 3-5 message pillars I should repeat in all content
```

---

## Stage 2 — Content Engine (re-run monthly)

**Agents:** Content Creator, Instagram Curator, TikTok Strategist, Visual Storyteller
**Output:** `02-content-calendar.md` (30-day calendar, hook bank, scripts)

```
Activate Content Creator (lead), with Instagram Curator, TikTok Strategist, and
Visual Storyteller.

Context: [paste 01-positioning.md]
My platforms: [your platforms]
Capacity: I can post [N] times/week and film [N] videos/week.

Produce a 30-day content engine:
- Content pillars mapped to my message pillars, with a posting cadence
- A 30-day calendar (date, platform, pillar, format, hook, CTA)
- A hook bank: 20 scroll-stopping hooks for fitness (myth-busting, transformation,
  day-in-the-life, client win, quick-win tip)
- 5 short-form video scripts (Reels/Shorts/TikTok) with shot list and on-screen text
- A repurposing workflow: one piece of pillar content -> 5 derivatives
- Compliant before/after / transformation framing (no unrealistic claims)
Every post must drive toward the lead magnet from my offer ladder.
```

---

## Stage 3 — Capture & Nurture (build once, refine quarterly)

**Agents:** Growth Hacker
**Output:** `03-funnel.md` (lead magnet, landing page copy, nurture sequence, referral loop)

```
Activate Growth Hacker.

Context: [paste 01-positioning.md]

Design my lead-capture funnel:
- A lead magnet that pre-qualifies (e.g. free 5-day challenge, "is group or 1:1
  right for you?" assessment, or a free intro class) tied to my offer ladder
- Landing page copy (headline, subhead, bullets, social proof slots, single CTA)
- A 5-message DM/email nurture sequence from opt-in -> booked consult
- A referral loop that turns current clients into a steady lead source
- 2 low-budget paid experiments I could test to accelerate, with success metrics
```

---

## Stage 4 — Convert & Measure (ongoing; review weekly)

**Agents:** Support Responder, Analytics Reporter
**Output:** `04-conversion-and-kpis.md` (inquiry scripts + KPI tracker)

```
Activate Support Responder, then Analytics Reporter.

Context: [paste 01-positioning.md and 03-funnel.md]

Support Responder: write my inquiry-handling playbook:
- DM/email response templates for common first-contact messages
- Objection handling (price, time, "I'm not fit enough yet", "does remote work?")
- A simple booking flow from "interested" to "consult scheduled"

Analytics Reporter: design a weekly KPI tracker for this funnel:
- Metrics by stage: reach -> profile visits -> leads -> consults booked ->
  show rate -> clients closed -> class/cohort fill rate -> revenue
- Targets for each, and a one-page weekly review ritual: what to look at, what
  to change when a number is off
```

---

## Run the whole engine at once (Orchestrator)

```
Activate Agents Orchestrator in NEXUS-Micro mode.

Mission: stand up a complete client-acquisition engine for my personal training
business and produce all four deliverables.

My business: [paste inputs.md]

Pipeline:
1. Positioning (Trend Researcher, Brand Guardian) -> 01-positioning.md
2. Content engine (Content Creator + Instagram Curator + TikTok Strategist +
   Visual Storyteller) -> 02-content-calendar.md
3. Capture & nurture (Growth Hacker) -> 03-funnel.md
4. Convert & measure (Support Responder, Analytics Reporter) -> 04-conversion-and-kpis.md

Each stage feeds the next. Quality gate between stages: every output must tie
back to my ICP and offer ladder. Keep claims realistic and compliant.
```

---

## The monthly loop

| Cadence | Do |
|---------|-----|
| Weekly | Review the KPI tracker; double down on the top-performing content format |
| Monthly | Re-run Stage 2 for a fresh 30-day calendar informed by last month's KPIs |
| Quarterly | Revisit positioning (Stage 1) and refine the funnel (Stage 3) |
