---
name: mr-interview-prep
description: Generate a complete Medical Representative (MR) interview preparation package — study guide and slide deck spec — for any drug or drug portfolio. Use this skill whenever the user wants to prepare a candidate for an MR job interview, mentions a drug name for interview prep, asks to build a study document for a pharmaceutical sales role, or wants an interview deck for a specific product. Triggers include: "prepare for MR interview", "study guide for [drug]", "interview deck for [drug]", "MR interview prep", or providing one or more drug names with context that an interview is upcoming. This skill covers any drug/therapeutic area — not limited to any single company or product class.
---

# MR Interview Prep Skill

## Purpose

Generate a complete, reusable interview preparation package for a Medical Representative (MR) job candidate, covering ANY drug or drug portfolio. This skill exists because the candidate's core weakness is **interview performance**, not product knowledge — every study guide and deck this skill produces must weight selling skills, objection handling, and stress-test readiness heavier than pure product facts.

Do not treat this as a "make a nice document" task. Treat it as building a weapon for someone who has failed multiple interviews already. Precision and directness beat completeness.

---

## Required Inputs (ask if not provided)

Before starting, confirm these from the user. If any are missing or ambiguous, ask — do not assume.

1. **Drug name(s)** — one or more. If more than one, determine relationship (see Multi-Drug Logic below).
2. **Target company** — name of the employer (e.g., DKSH, Zuellig Pharma, manufacturer-direct). If unknown yet, proceed with study guide; company is only required at deck stage.
3. **Interview format** — who's interviewing (SM, HR, panel, technical), language of interview, time available before the interview.
4. **Territory / hospital context** — if known. Do NOT invent hospital names or assume territory scope not confirmed by the user. If only an anchor hospital is known, scope the deck to specialties, not hospital names (see Deck Spec section).
5. **Candidate's prior experience** — pull from memory/project files if available (e.g., prior internship, prior interview attempts, known weaknesses). Do not re-ask for info already known from context.

If drug names are the only input given, proceed to Phase 1 with reasonable defaults and flag any assumptions made.

---

## Workflow — 3 Phases

### Phase 1 — Study Guide (always generate first)

Triggered automatically once drug name(s) are provided. Do not wait for explicit permission to build the study guide — this is the default first deliverable.

Output: DOCX (or MD if user prefers), following the **Study Guide Template** below.

After generating, stop. Do not proceed to deck creation. Tell the user the study guide is ready and that the deck can be built whenever they're ready.

### Phase 2 — Deck Confirmation (only when user asks for a deck)

When the user asks for a slide deck, DO NOT build immediately. First confirm:
- **Company name** (if not already known) → determines color theme
- **Slide count / template** — default is the 8-slide structure below; ask if user wants to cut/adjust
- **Layout style** — confirm against the Deck Spec Template below, flag any drug-specific slides that need adjustment (Slides 3, 4, 5 are always drug-specific)
- **Color theme** — confirm hex codes matching company branding

Summarize the plan and ask for explicit go-ahead before generating the deck spec.

### Phase 3 — Deck Spec Generation

Output: a markdown build-spec file (NOT a live PPTX) formatted for consumption by the user's separate slide-deck-building skill/tool in Claude Code. Follow the **Deck Spec Template** below exactly — this keeps output format consistent across every drug so the downstream deck-builder skill always knows what to expect.

---

## Multi-Drug Logic

Determine relationship between drugs BEFORE writing content:

**Connected/Portfolio drugs** (same manufacturer, same disease area, used in sequence or combination — e.g., Lantus → Toujeo → Soliqua):
- Frame as a **patient journey / treatment ladder**, not competing options
- Use bridge sentences connecting each product's role in the journey
- Single unified study guide and deck covering all drugs together
- Competitive landscape slide covers the portfolio as a whole vs external competitors

**Unrelated/Standalone drugs** (different manufacturers, different disease areas, or candidate is comparing job offers for different roles):
- Treat as **fully separate study guides and decks**
- Do not force artificial connections
- If in the same conversation, clearly separate outputs by drug with distinct file names

If relationship is unclear, ask the user directly: "Are these drugs part of one portfolio/role, or separate interview opportunities?"

---

## Study Guide Template (fixed structure — always these 5 sections)

Language: match what the user specifies (Thai-only, English-only, or bilingual with English technical terms — confirm if not stated). Do not assume Thai by default; ask.

### Section 1 — Product Knowledge
- Overview table: generic name, brand, drug class, formulation, dosing
- Mechanism of Action — plain-language explanation, key pharmacology facts
- Approved indications — numbered, with dosing specifics per indication
- Key differentiators vs. 2–3 main competitor classes (structured as comparison call-outs, not just a data dump)
- Contraindications & precautions — practical, not exhaustive textbook copy
- Territory/hospital context — ONLY if user has confirmed real territory info; otherwise omit this subsection entirely rather than guessing

### Section 2 — Detailing Script
- One core selling framework, applied consistently across all future guides for this skill (default: ADAPT — Assess, Discover, Activate, Project, Tie Down; use Sales Process cycle model — Opening→Probing↔Presentation→Closing — if the user's example materials indicate that's the preferred framework instead. Confirm which framework once, then reuse it as default for all future runs of this skill unless told otherwise.)
- Full example script for one realistic physician scenario relevant to the drug's primary indication
- 2–3 bridge sentences connecting candidate's prior real experience to this new drug/role (pull specifics from candidate's known background — do not write generic placeholders)

### Section 3 — Objection Handling
- Minimum 5 objections specific to this drug/market (price, competitor loyalty, formulary inertia, patient-level concerns, "I don't have time")
- Each objection following: Acknowledge → Clarify → Respond → Confirm structure
- Written as full scripted responses, not bullet-point talking points — candidate needs to be able to read this and internalize actual phrasing

### Section 4 — SM/Interviewer-Level Q&A
- Self & motivation questions (tell me about yourself, why this company, strengths/weaknesses)
- Commercial/territory questions (how would you start, how do you handle non-adopters, what do you know about the company)
- One "sell me this drug in 60 seconds" cold-sell prompt with model answer

### Section 5 — Mock Interview Stress Bank (mandatory — this is the section that addresses her actual failure pattern)
- Minimum 8–10 adversarial/curveball questions designed to destabilize a nervous candidate:
  - Direct challenges to credibility ("you only interned 5 months, what do you actually know?")
  - Rejection-probing ("why didn't the other companies hire you?")
  - Pressure/composure tests ("this job requires 6-day weeks, are you sure you can handle it?")
  - Silence/pause bait — questions designed to see if she fills awkward silence with over-talking
  - Rapid-fire follow-ups to a single answer (simulate SM pushing back twice on the same point)
- Each with a model answer AND a one-line coaching note on delivery (tone, pacing, what NOT to do)
- Close this section with a explicit checklist: composure cues to self-monitor for (talking too much, not listening, over-explaining, defensiveness)

### Closing Checklist
- One-page condensed "read this before you walk in" summary
- Max 10 bullet points, pulls the single most important fact from each section above

---

## Deck Spec Template (fixed 8-slide structure — default, user may cut slides manually)

Output format: markdown build-spec, NOT a generated PPTX file. This feeds into the user's separate deck-building skill.

Always confirm company name and color theme before generating this. Structure:

```
# [Drug Name] Interview Deck – Build Spec

## Context
[Candidate name, company, role, territory if known, interview format, language]

## Theme
[Hex codes, font, slide size 16:9]

## Slide 1 – Hello, I'm [Name]
[Photo placeholder, 3 pillars: Pharma Background / Field Experience / Why This Company]

## Slide 2 – What I Did (Experience)
[3 experience cards from candidate's real background — pull from known project context, do not invent]

## Slide 3 – Product Knowledge [DRUG-SPECIFIC]
[3-column: MOA / Key Indications / Key Differentiators — no trial data on slide, verbal only]

## Slide 4 – Target Physician Specialties [DRUG-SPECIFIC]
[4–5 specialty cards, Tier A/B, NO hospital names unless confirmed territory]

## Slide 5 – Competitive Landscape & Positioning [DRUG-SPECIFIC]
[Competitor table + "Wins When" positioning box + one-line tagline]

## Slide 6 – Selling Approach
[Visual flow of confirmed selling framework — Sales Process or ADAPT]

## Slide 7 – Strengths, Development Areas & Why Me
[3 strengths / 2 honest development areas with mitigation / closing bar statement]

## Slide 8 – Closing (optional — mark as cuttable)
[Thank you, contact block, tagline]

## Notes for deck-builder skill
- All content in [language]
- Primary color: [hex]
- Font: [font]
- Export filename: [Drug]_Interview_Deck_[CandidateName].pptx
```

Slides 1, 2, 6, 7 stay structurally identical across all drugs — only the content specifics change. Slides 3, 4, 5 are rebuilt from scratch every time based on the new drug's actual product/market facts. Never carry over competitor or specialty data from a previous drug's deck.

---

## Standing Defaults (carry forward across all runs of this skill unless user overrides)

- Selling framework: confirm once with user, then reuse as default
- Language: confirm once with user, then reuse as default (still confirm per-project since interview language can vary by company)
- Slide count: 8, user trims manually
- Study guide format: DOCX unless user says MD
- Deck output: markdown spec only, never a live PPTX from this skill directly

## When NOT to Use This Skill

- If the user wants general pharma industry knowledge unrelated to an upcoming interview → answer directly, don't invoke this skill
- If the user wants deep clinical/scientific research on a drug for reasons unrelated to job interview prep → treat as a normal research request
- If territory/hospital details are being guessed or invented rather than confirmed by the user → stop and ask, do not fabricate

## Honest Mentor Note (keep in mind while executing, don't skip this)

This skill produces preparation materials. It does not fix live interview performance on its own. If the candidate has failed multiple interviews despite adequate preparation, the study guide and deck are necessary but not sufficient — recommend to the user that mock interview practice with real-time feedback (video review, timed pressure Q&A, actual role-play with objection pushback) happens *after* this material is built, not instead of it. Flag this explicitly at the end of Phase 1 output if it hasn't already been addressed in the conversation.
