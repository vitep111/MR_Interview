# MR_Interview

Preparation workspace for **Medical Representative (MR)** pharmaceutical sales
interviews. It bundles two Claude Code skills that together take you from a drug
name to a finished interview package:

- **`mr-interview-prep`** — generates the interview study guide (product knowledge,
  detailing script, objection handling, SM/interviewer Q&A, and a mock-interview
  stress bank) and an 8-slide deck **build-spec**, for any drug or portfolio.
- **`ppt-master`** — turns a build-spec (or any source document) into an actual
  `.pptx` deck.

## Layout

```
.claude/skills/
  mr-interview-prep/     # study guide + deck-spec generator
  ppt-master/            # SVG-based PPTX builder
CLAUDE.md                # repo guidance Claude follows automatically
```

## Usage

Open this repo in Claude Code and describe what you need, e.g.:

- "Prepare me for an MR interview on Toujeo" → runs `mr-interview-prep` (study guide first).
- "Now build the deck" → `mr-interview-prep` produces the deck build-spec.
- "Create the PPT from this spec" → `ppt-master` exports the `.pptx`.

The skills auto-trigger on those phrasings; see `CLAUDE.md` and each skill's
`SKILL.md` for the full workflow and templates.

## Credits

`ppt-master` is vendored from https://github.com/vitep111/ppt-master.
