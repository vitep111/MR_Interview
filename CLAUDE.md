# MR_Interview — Medical Representative Interview Preparation

This repository is a working environment for preparing a candidate for **Medical
Representative (MR)** job interviews in the pharmaceutical industry. It holds the
skills, generated study guides, and slide-deck specs used to get the candidate
interview-ready for any drug or drug portfolio.

## What this repo is for

The candidate's core weakness is **interview performance**, not product knowledge.
Everything produced here must weight selling skills, objection handling, and
stress-test readiness heavier than pure product facts. Treat each deliverable as a
tool for someone who has already failed multiple interviews — precision and
directness beat completeness.

## Skills installed here

| Skill | Location | Use it when |
|-------|----------|-------------|
| `mr-interview-prep` | `.claude/skills/mr-interview-prep/SKILL.md` | Building an interview prep package (study guide + deck spec) for any drug. Triggers: "prepare for MR interview", "study guide for [drug]", "interview deck for [drug]". |
| `ppt-master` | `.claude/skills/ppt-master/SKILL.md` | Turning a deck build-spec (or any source document) into an actual PPTX. Triggers: "create PPT", "make presentation", "生成PPT", "ppt-master". |

## How the two skills work together

1. `mr-interview-prep` produces a **markdown deck build-spec** (it never generates a
   live PPTX itself — see its Phase 3 / Standing Defaults).
2. `ppt-master` consumes that build-spec (or any source doc) and produces the actual
   **PPTX** deck.

So the normal flow is: **drug name → `mr-interview-prep` study guide → deck build-spec
→ `ppt-master` → PPTX**.

## Working conventions

- **Never fabricate** hospital names, territory scope, trial data, or candidate
  background. If a required input is missing or ambiguous, ask — do not assume.
  This applies to both skills.
- **Language**: confirm per project (Thai-only / English-only / bilingual). Do not
  default to Thai.
- Generated study guides, deck specs, and exports should be kept out of version
  control unless the user asks to commit a specific deliverable (see `.gitignore`).
- Follow the full workflow and templates defined inside each skill's `SKILL.md`
  rather than improvising structure.
