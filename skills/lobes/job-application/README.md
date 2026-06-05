# Job Application

> A personalized daily job scan that scores postings against your resume and pre-fills application forms up to the final submit, so you finish each one in a click or two.

## Install

Paste into your AI chat:

```
Read https://raw.githubusercontent.com/spacecowboyian/brains-skills/main/skills/lobes/job-application/skill.md
then set up the Job Application skill in my Brains knowledge base.
```

## What this skill does

Turns the daily grind of job hunting into a repeatable workflow that gets smarter every run. Your resume fills most of it; you confirm the rest once.

- **Onboards from your resume** — indexes your resume, builds a reusable seeker profile (contact, work history, work authorization, target pay, education, screening answers, editable essay templates), and interviews you for the few things a resume never contains.
- **Scans job boards** — searches each enabled site for your target roles and locations, reads the full description for each posting, and skips anything it already processed.
- **Scores honestly** — builds a requirements matrix for every job (required vs. preferred qualifications, met / partial / no) and computes a fit percentage, weighting required qualifications heavier. Conservative by design, so it does not over-prep bad fits.
- **Preps applications** — for jobs at or above your threshold, it pre-fills the live application form from your profile and drafts tailored answers, leaving the resume upload, consent, and final submit for you.
- **Learns each site** — keeps a profile per job board (how to search and read it) and per application system (how to fill its form, and its gotchas) so the next run gets it right the first time.
- **Delivers a morning digest** — scanned count, the prepped matches with apply links and blockers, and a skip count.

## Example queries

> "Set up my job search — here's my resume."

> "Run my daily job scan and prep anything that's a strong fit."

> "Score this posting against my resume: <url>"

> "Add Wellfound as a search site."

> "Prep an application for this Greenhouse job and tell me what's left for me to do."

## Files

| File | Purpose |
|---|---|
| `skill.md` | Install file — agent instructions + page template combined |
| `skill.json` | Machine-readable manifest |
| `template.md` | The job-application page template |
| `instructions.md` | Agent instructions (standalone) |
| `README.md` | This file |

## License

MIT
