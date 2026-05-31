# Shopping List

> Auto-categorized shopping lists with one-time online price research and a preferred brands memory layer that gets smarter with every purchase.

## Install

Paste into your AI chat:

```
Read https://raw.githubusercontent.com/spacecowboyian/brains-skills/main/skills/lobes/shopping-list/skill.md
then set up the Shopping List skill in my Brains knowledge base.
```

## What this skill does

Turns free-form "I need to buy X, Y, Z" input into organized, persistent shopping lists — sorted by category, with live price research for online purchases and a memory layer that remembers which brands you actually buy.

- **Auto-categorization** — parse any shopping input (voice memo, chat) and route each item to the right list: Grocery, Hardware, Auto Parts, Online, or a new category if none fit
- **Online price research** — for items classified as "buy online," the agent searches for the top 3 sellers, notes price and rating, and recommends the best value with a one-sentence reason — at add time only (no background refresh)
- **Preferred brands memory** — when you mark an item purchased, the agent records the brand. Next time you add that item, it pre-fills the preferred brand automatically

## Example: mixed item list

> **You say:** "I need to get apples, oranges, a wireless mouse, a birthday cake, a PCV valve for my 85 MR2, and a pack of light bulbs."

**Agent routes:**

`shopping/grocery.md` — Apples, oranges, birthday cake  
`shopping/hardware.md` — Light bulbs  
`shopping/auto-parts.md` — PCV valve for 85 MR2  
`shopping/online.md` — Wireless mouse (+ price research):

```
- [ ] Wireless mouse *(researched 2026-05-31)*
  - Amazon — $24.99, 4.7★ — **Best value:** Prime eligible, ships free
  - Best Buy — $27.99, 4.6★
  - B&H Photo — $26.50, 4.5★
```

## Example: preferred brands flow

**First purchase:**

> **You:** "I bought the peanut butter — went with Jif."  
> **Agent:** Moves "peanut butter" to `## Purchased` on grocery.md, records in preferred-brands.md:

| Item type | Preferred brand/product | Last purchased | Notes |
|-----------|------------------------|----------------|-------|
| Peanut butter | Jif | 2026-05-31 | Best value pick |

**Next time:**

> **You:** "Add peanut butter to the grocery list."  
> **Agent:** Adds "Jif peanut butter *(preferred — last bought 2026-05-31)*" — no need to specify the brand again.

## Files

| File | Purpose |
|------|---------|
| [`skill.md`](skill.md) | Install file — agent instructions + all templates combined |
| [`skill.json`](skill.json) | Metadata manifest |
| [`template.md`](template.md) | Category list page template (standalone) |
| [`instructions.md`](instructions.md) | Agent instructions (standalone) |

## License

[MIT](../../LICENSE)
