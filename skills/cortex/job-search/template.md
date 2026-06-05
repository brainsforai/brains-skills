# Job Search — Working-Memory Pages

A cortex keeps its state in the vault. Unlike a lobe (one template for one record), a cortex maintains several **working-memory** page types that it reads and updates every run, and it spawns `job-application` lobe pages as the record of prepped jobs. These are the working-memory templates. Default location is a `job-search/` project; if a hippocampus skill is active, ask it where each page belongs and record that in `filed_at`.

---

## Seeker profile → `job-search/seeker-profile.md`

Your source of truth for filling forms. One per user. Never invent values; leave unknowns blank and flag them. Also holds the run config: target roles/locations, enabled sites, and the fit threshold.

```markdown
---
file_type: job-search-seeker-profile
filed_at: ""               # set by the active hippocampus; default job-search/seeker-profile.md
title: "Seeker profile"
fit_threshold: 85          # % at/above which a job is auto-prepped
target_roles: []
target_locations: []
enabled_search_sites: []   # e.g. [linkedin]
tags: [job-search]
---

## Contact
| Field | Value |
|---|---|
| Full name | |
| Email | |
| Phone | |
| Location (city, state) | |
| LinkedIn / GitHub / portfolio | |
| Current / most recent title | |

## Work authorization
- Authorized to work in <country>:
- Requires sponsorship (now / future):

## Compensation
- Target range:
- Single value for a free-text salary box:

## Location / remote preference
- Remote / hybrid / onsite:
- Hard requirements (e.g. remote only):
- Willing to relocate:

## Education
- School / degree / field / dates:

## Voluntary self-identification (optional surveys)
- Whether the user answers these:
- Values (only if the user opts in):

## Standard screening answers
- Bachelor's degree · years-of-experience band · related to a current employee · authorized to work · needs sponsorship

## Writing preferences for application text
- Tone / hard rules (e.g. no invented metrics):
- Positioning one-liner:

## Reusable long-form answers (editable starting points)
### "What motivated you to apply?" (adapt per company)
>
### Domain / experience paragraph
>

## Resume
- Brains copy: job-search/resume.md
- Exact PDF filename the user uploads:   <!-- forms need a PDF upload; the user uploads it, never you -->
```

---

## Search-site profile → `job-search/search-sites/<site>.md`

One per job board. How to **search and read** listings here, so the next run gets it right the first time. (Filling the form is a separate application-site profile.)

```markdown
---
file_type: job-search-search-site
filed_at: ""               # default job-search/search-sites/<site>.md
title: ""                  # site name
base_url: ""
login_required: false
tags: [job-search, search-site]
---

## Running a scoped search
- The search URL pattern and the parameters that matter (keywords, location, remote filter, date window, sort).
- Keyword tricks that cut noise (e.g. exact-phrase quoted titles vs. broad terms).
- How many results per page / how to paginate.

## Reading a full job description reliably
- The method that actually returns the full description, and any rendering quirks (lazy/virtualized lists, slow promoted listings).

## Gotchas / dos and don'ts
- Virtualization, rate limits, stale panes — anything that wasted time the first time.

## Method that worked (sequence)
- The concrete steps that succeeded, so they can be replayed.

## How a listing reaches an application form
- Whether Apply stays on-site or redirects to an external system (name it → use that application-site profile).
```

---

## Application-site profile → `job-search/application-sites/<system>.md`

One per application system. How to **fill that system's form**. Read the matching profile before filling any form on that system.

```markdown
---
file_type: job-search-application-site
filed_at: ""               # default job-search/application-sites/<system>.md
title: ""                  # application-system / domain name
url_pattern: ""
tags: [job-search, application-site]
---

## What to expect
- How you reach the form (redirect / new tab / inline). Single page vs. multi-step. Where the final Submit is.

## Field list (in order)
- Each field, its value source (from the seeker profile), and the widget type (text / native select / custom dropdown / radio / file upload / consent).

## Gotchas (the high-value part)
- Custom dropdowns / type-ahead widgets often reject a typed value — open the dropdown and click the option, or flag it for the user.
- Fields that re-render and stale their refs after another field changes (set order matters).
- Cookie banners, validation that clears on save.

## Method that worked (sequence)
- The concrete steps that succeeded the first time.

## Left for the user (always)
- Resume upload, account/login, consent/terms/SMS, final Submit, and any personal field not in the profile.
```

---

## Skip log → `job-search/skipped-log.md`

One running log of below-threshold / disqualified jobs so they're never reprocessed. Append one line per skip — never a page per skip.

```markdown
---
file_type: job-search-skip-log
filed_at: ""               # default job-search/skipped-log.md
title: "Skipped jobs log"
tags: [job-search]
---

| Date | Company | Title | URL | Score | Reason |
|---|---|---|---|---|---|
```

---

## The record it spawns: `job-application` (a lobe)

For each at/above-threshold job, this cortex spawns one **`job-application`** page — that lobe is the record of a prepped application (fit matrix, score, comp, drafted answers, apply URL, steps remaining for the human). Install the `job-application` lobe alongside this cortex; the cortex decides *what to do*, the lobe holds *what* each prepped job contains, and the active hippocampus decides *where* it's filed.
