# Restaurant Review

> Log every meal experience and answer "what should I eat tonight?" with ranked, dish-level recommendations from your own history.

## Install

Paste into your AI chat:

```
Read https://raw.githubusercontent.com/spacecowboyian/brains-skills/main/skills/lobes/restaurant-review/skill.md
then set up a new project in my Brains knowledge base using this skill.
```

## What this skill does

Sets up a single meals page (`food/meals.md`) and an agent configured to work with it. The agent captures meal experiences from voice memo or freeform chat, prompts for anything missing, and writes clean structured entries. Once you have entries, it answers food queries with dish-level reasoning drawn from your personal history.

**Capture:**
- Extracts restaurant, date, location, dishes, rating, craveability, and verdict from natural language
- Generates a stable restaurant slug so repeat visits stay grouped (`pizza-shoppe` across all your Pizza Shoppe visits)
- Asks one question at a time for any missing required field — never dumps a list

**Query:**
- Ranks restaurants by rating, craveability, and recency when you ask what to eat
- Surfaces dish-level reasons, not just names
- Excludes places you've written off

## Example: voice memo → entry

**User:** "Just ate at Pizza Shoppe. Had the white clam pizza — incredible, briny and perfectly charred. Also got the arancini, solid but not the reason to go back. 9 out of 10, would absolutely go back for that pizza."

**Agent:** "When did you eat there?"

**User:** "Last night, May 30th."

**Agent:** "What city or neighborhood?"

**User:** "New Haven."

**Agent:** "Any dishes you'd specifically crave and come back for?"

**User:** "Definitely the white clam pizza."

**Agent appends to `food/meals.md`:**

```markdown
---

## Pizza Shoppe — 2026-05-30
**slug:** pizza-shoppe
**Location:** New Haven, CT
**Cuisine:** Pizza
**Visited with:** solo

### What I had
- **White clam pizza** — incredible, briny and perfectly charred
- **Arancini** — solid but not the reason to go back

### Rating: 9/10
### Craveability
- **Would I crave this?** Yes
- **Crave-worthy dishes:** white clam pizza
- **Unique to this place?** Yes

### Verdict
Go back for the white clam pizza — one of the best things I've eaten.
```

## Example: query → ranked recommendations

**User:** "What should I eat tonight?"

**Agent:**
> 1. **Pizza Shoppe** — 9/10, the white clam pizza is crave-worthy and unique to that place. Last entry 2 days ago.
> 2. **Taco Lugar** — 8/10, al pastor tacos were a standout. Haven't been in 6 weeks.
> 3. **Ramen House** — 7/10, the spicy miso ramen is worth craving. Last entry 2 months ago.

## Example queries

- `I just ate at [restaurant] — let me tell you about it`
- `What should I eat tonight?`
- `Where should we go for dinner — I want something I'd actually crave`
- `What's a place I haven't been in a while?`
- `What are my highest-rated restaurants?`
- `What's the best dish I've eaten recently?`

## Notes

- **One page, all entries.** Every visit goes into `food/meals.md`, appended newest first. No per-restaurant pages.
- **Slug reuse.** Repeat visits to the same restaurant get the same slug, so they stay grouped in search.
- **No partial entries.** The agent asks for missing fields one at a time before writing anything.

## Files

| File | Purpose |
|------|---------|
| [`skill.md`](skill.md) | Install file — agent instructions + template combined |
| [`skill.json`](skill.json) | Metadata manifest |
| [`template.md`](template.md) | Page template (standalone) |
| [`instructions.md`](instructions.md) | Agent instructions (standalone) |

## License

[MIT](../../LICENSE)
