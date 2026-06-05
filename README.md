# brains-skills

> A community library of domain-specific knowledge base skills for [Brains](https://usebrains.app).

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

Each skill is a self-contained folder: a `skill.md` you point your AI at, a page template to drop into your knowledge base, and a manifest. Five minutes from zero to a fully wired knowledge domain.

Skills come in three kinds:

- **Hippocampus** — whole-vault *filing systems*. They decide **where** a page belongs. Pick **one** (or none).
- **Lobes** — note *templates* for one type of record. They decide **what** a page contains. Use **many**.
- **Cortex** — *agents* that run a goal over time. They decide **what to do, when, and how** — acting across sessions and spawning lobe pages as the record of their work. Use **as needed**.

A lobe defines a note's fields; it never picks a folder. At create time it asks the active hippocampus skill where to file the page and records that path in the page's `filed_at` field. With no hippocampus active, a lobe falls back to a flat `<skill-id>/` folder. The three compose, mapping to the brain: lobe = *what*, hippocampus = *where*, cortex = *what to do* (the executive layer that pursues a goal and produces lobe pages as its record).

---

## Skills

### 🧭 Hippocampus — filing systems (pick one)

| Skill | Description | `skill.md` |
|-------|-------------|------------|
| [para](skills/hippocampus/para/) | Organize everything into Projects, Areas, Resources, Archives by actionability | [→ raw](https://raw.githubusercontent.com/spacecowboyian/brains-skills/main/skills/hippocampus/para/skill.md) |
| [johnny-decimal](skills/hippocampus/johnny-decimal/) | Give every page a unique numeric ID in a strict two-level hierarchy | [→ raw](https://raw.githubusercontent.com/spacecowboyian/brains-skills/main/skills/hippocampus/johnny-decimal/skill.md) |
| [zettelkasten](skills/hippocampus/zettelkasten/) | Atomic, linked notes where connections surface emergent insight | [→ raw](https://raw.githubusercontent.com/spacecowboyian/brains-skills/main/skills/hippocampus/zettelkasten/skill.md) |
| [mind-palace](skills/hippocampus/mind-palace/) | Store and retrieve knowledge spatially via the method of loci | [→ raw](https://raw.githubusercontent.com/spacecowboyian/brains-skills/main/skills/hippocampus/mind-palace/skill.md) |
| [operator](skills/hippocampus/operator/) | Project-scoped layout for running many concurrent projects: per-project state, hub-and-spoke open loops, write-time synthesis | [→ raw](https://raw.githubusercontent.com/spacecowboyian/brains-skills/main/skills/hippocampus/operator/skill.md) |

### 🧩 Lobes — note templates (use many)

| Skill | Description | `skill.md` |
|-------|-------------|------------|
| [book-notes](skills/lobes/book-notes/) | Capture and query book insights, quotes, and takeaways | [→ raw](https://raw.githubusercontent.com/spacecowboyian/brains-skills/main/skills/lobes/book-notes/skill.md) |
| [weekly-review](skills/lobes/weekly-review/) | Reflect on each week and synthesize into next actions | [→ raw](https://raw.githubusercontent.com/spacecowboyian/brains-skills/main/skills/lobes/weekly-review/skill.md) |
| [meeting-notes](skills/lobes/meeting-notes/) | Structured meeting records with decisions and action items | [→ raw](https://raw.githubusercontent.com/spacecowboyian/brains-skills/main/skills/lobes/meeting-notes/skill.md) |
| [project-tracker](skills/lobes/project-tracker/) | Track project status, blockers, risks, and team | [→ raw](https://raw.githubusercontent.com/spacecowboyian/brains-skills/main/skills/lobes/project-tracker/skill.md) |
| [recipes](skills/lobes/recipes/) | Personal recipe database with meal planning support | [→ raw](https://raw.githubusercontent.com/spacecowboyian/brains-skills/main/skills/lobes/recipes/skill.md) |

### ⚙️ Cortex — agents (run a goal over time)

| Skill | Description | `skill.md` |
|-------|-------------|------------|
| [job-search](skills/cortex/job-search/) | Daily job-search agent: scan your boards, score each posting against your resume, and pre-fill strong-fit applications up to the final click — spawning a [job-application](skills/lobes/job-application/) page per match | [→ raw](https://raw.githubusercontent.com/spacecowboyian/brains-skills/main/skills/cortex/job-search/skill.md) |

---

## Quick install

Paste into your AI chat — replace `<group>/<skill-id>` with `hippocampus/<name>`, `lobes/<name>`, or `cortex/<name>` from the tables above:

```
Read https://raw.githubusercontent.com/spacecowboyian/brains-skills/main/skills/<group>/<skill-id>/skill.md
then set up a new project in my Brains knowledge base using this skill.
```

**Example — recipes (a lobe):**

```
Read https://raw.githubusercontent.com/spacecowboyian/brains-skills/main/skills/lobes/recipes/skill.md
then set up a new project in my Brains knowledge base using this skill.
```

That's it. The `skill.md` file contains everything the AI needs: agent instructions and the page template.

> **Note:** Use the `raw.githubusercontent.com` URL, not the GitHub browse URL. Raw URLs fetch directly without search indexing or scraping.

---

## How it works

Each skill folder contains:

```
skills/<group>/<skill-id>/      ← group is `hippocampus`, `lobes`, or `cortex`
  skill.md          ← The install file. Agent instructions + page template, combined.
  skill.json        ← Machine-readable manifest (name, version, type, fields, tags).
  template.md       ← Page template only (frontmatter + sections). For a cortex: its working-memory pages.
  instructions.md   ← Agent instructions only.
  README.md         ← Human docs, capabilities, example queries.
```

`skill.json` carries a `"type"` field — `"hippocampus"`, `"lobe"`, or `"cortex"` — so tools can route automatically; the folder grouping mirrors it for humans browsing the repo.

`skill.md` is the primary artifact. Share it with your AI and it knows how to set up the project, create pages, and answer queries in that domain.

`template.md` and `instructions.md` exist as standalone files for users who want to copy-paste them individually or use them outside a Brains workflow.

---

## Manual install (copy-paste)

If you'd rather not use the AI prompt:

1. Copy `template.md` from the skill folder into your Brains pages folder
2. Copy `instructions.md` into your AI's instructions file (e.g. `brainsapp-claude.md`)
3. Start creating pages using the template

No CLI, no build step.

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for the skill structure spec and submission process.

---

## License

[MIT](LICENSE)
