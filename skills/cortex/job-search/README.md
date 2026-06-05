# Job Search

> A daily job-search agent: scan your boards, score each posting against your resume, and pre-fill strong-fit applications up to the final click — spawning a job-application record for each.

**Kind:** cortex — an agent that runs a goal over time (*what to do, when, and how*). Best run in an agent host with **browser automation and persistent memory** (e.g. Claude Cowork): browser control to read job boards and fill forms, and a connected vault so each stateless run reloads full context and gets smarter.

## Install

```
Read https://raw.githubusercontent.com/spacecowboyian/brains-skills/main/skills/cortex/job-search/skill.md
then set up a new job search in my Brains knowledge base using this skill.
```

Also install the **[job-application](../../lobes/job-application/)** lobe — it's the record this cortex spawns for each prepped job.

## What this skill does

- **Onboards you once** — indexes your resume, builds a reusable seeker profile, and interviews for what a resume lacks (target pay, work authorization, remote requirement, EEO preferences, fit threshold).
- **Runs a daily loop** — load profiles → scan enabled boards → score each posting with a requirements matrix (required vs. preferred, partial = 0.5, required weighted heavier, conservative) → for fits at/above threshold (default 85%) pre-fill the live form and spawn a `job-application` page → log sub-threshold jobs to a skip log → deliver a digest.
- **Learns over time** — keeps a profile per job board (how to search and read it) and per application system (how to fill its form), so each run is faster and more accurate.
- **Stays inside guardrails** — never clicks the final submit, uploads your resume file, creates accounts or logs in, ticks consent boxes, or invents values. You own every irreversible click.

## Example queries

- "Onboard me — here's my resume; set up my job search."
- "Run my job search and prep anything at 85% or above."
- "Add Wellfound as a search site and teach yourself how to search it."
- "Score this posting against my resume and show me the matrix."
- "Give me this morning's digest of prepped matches and skips."

## Files

| File | Purpose |
|---|---|
| `skill.md` | The install file — agent instructions + working-memory page templates, combined. |
| `skill.json` | Machine-readable manifest (`type: cortex`, spawns `job-application`). |
| `template.md` | The cortex's working-memory page templates (seeker / search-site / application-site / skip log). |
| `instructions.md` | Agent instructions only — the action loop and guardrails. |
| `README.md` | This file. |

## License

MIT
