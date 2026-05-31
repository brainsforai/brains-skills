# Shopping List Skill

**Skill ID:** shopping-list  
**Version:** 1.0.0  
**Domains:** personal, productivity  
**Install:** fetch this file and follow the "How to use" section

## How to use

Read this file, then set up the shopping list knowledge base in the user's Brains instance. Create the following pages using the templates below: `shopping/index.md`, `shopping/grocery.md`, `shopping/hardware.md`, `shopping/auto-parts.md`, `shopping/online.md`, and `shopping/preferred-brands.md`. Once created, follow the agent instructions to handle any items the user wants to add.

**Filing:** The default folder for all pages is `shopping/`. If a hippocampus skill (PARA, Johnny.Decimal, etc.) is active, ask it where to file the pages and record the path in each page's `filed_at` field.

---

## Agent Instructions

You help the user maintain smart, organized shopping lists across multiple category pages. This lobe is multi-page: each shopping category lives in its own page (e.g. `shopping/grocery.md`), with a master index at `shopping/index.md` and a preferred brands memory page at `shopping/preferred-brands.md`.

### Adding items

When the user mentions items to buy — via voice transcript, chat, or a list — do this for each item:

**1. Check preferred brands.** Before categorizing, look up the item in `shopping/preferred-brands.md`. Use judgment, not exact matching — "PB", "peanut butter", and "Jif" all resolve to the same entry. If a preferred brand is found, substitute it: "peanut butter" becomes "Jif peanut butter *(preferred — last bought YYYY-MM-DD)*".

**2. Categorize using judgment.** Infer the right list from the item's nature — do not use a lookup table:
- Perishables, food, household consumables → Grocery
- Building materials, paint, tools, fasteners → Hardware
- Vehicle parts, fluids, filters → Auto Parts
- Electronics, specialty goods, hard-to-find items best bought online → Online
- Anything that doesn't fit the above → create a new category page named after the inferred type

**3. Append to the category page.** Add the item as a `- [ ] Item name` checklist entry under a `## Added YYYY-MM-DD` section. If the category page doesn't exist, create it from the template and add a row to `shopping/index.md`.

**4. For Online items only — run price research.** Search `"{item name} buy online best price"`, find the top 3 sellers, and record each with price and rating. Select the best-value option and explain why in one sentence. Format:

```
- [ ] Wireless mouse *(researched YYYY-MM-DD)*
  - Amazon — $24.99, 4.7★ — **Best value:** Prime eligible, ships free
  - Best Buy — $27.99, 4.6★
  - B&H Photo — $26.50, 4.5★
```

Do not run price research for Grocery, Hardware, or Auto Parts items.

### Marking items purchased

When the user marks an item purchased (checks it off or says "I bought X"):

1. Move the entry to a `## Purchased` section at the bottom of the same list page with a purchase date: `- [x] Jif peanut butter *(purchased YYYY-MM-DD)*`
2. Upsert a row in `shopping/preferred-brands.md`:

| Item type | Preferred brand/product | Last purchased | Notes |
|-----------|------------------------|----------------|-------|
| Peanut butter | Jif | YYYY-MM-DD | Best value pick |

If the item on the list was generic (no brand specified), ask which brand was purchased before recording. If the user buys a *different* brand than the preferred one, ask: "Want me to update your preferred brand for [item] to [new brand]?" — update only on confirmation.

### Output format

- Keep item entries concise. Lead with the item name.
- Use `## Added YYYY-MM-DD` headings to group new additions by date.
- For Online items, indent the price research lines under the checklist entry (two spaces).
- Never ask multiple questions at once. If clarification is needed, ask for the most important field first.

---

## Page Templates

### shopping/index.md

```markdown
---
file_type: shopping-list
filed_at: ""
title: Shopping Lists
tags: [shopping]
---

# Shopping Lists

| List | Page |
|------|------|
| Grocery | [grocery.md](grocery.md) |
| Hardware | [hardware.md](hardware.md) |
| Auto Parts | [auto-parts.md](auto-parts.md) |
| Online | [online.md](online.md) |
```

*(Agent appends new rows when new category pages are created.)*

---

### shopping/grocery.md

```markdown
---
file_type: shopping-list
filed_at: ""
title: Grocery List
tags: [shopping, grocery]
---

# Grocery List

## Added YYYY-MM-DD

- [ ] Item

## Purchased
```

---

### shopping/hardware.md

```markdown
---
file_type: shopping-list
filed_at: ""
title: Hardware List
tags: [shopping, hardware]
---

# Hardware List

## Added YYYY-MM-DD

- [ ] Item

## Purchased
```

---

### shopping/auto-parts.md

```markdown
---
file_type: shopping-list
filed_at: ""
title: Auto Parts List
tags: [shopping, auto-parts]
---

# Auto Parts List

## Added YYYY-MM-DD

- [ ] Item

## Purchased
```

---

### shopping/online.md

```markdown
---
file_type: shopping-list
filed_at: ""
title: Online List
tags: [shopping, online]
---

# Online List

Items here include price research from the date they were added. Revisit manually for updated prices.

## Added YYYY-MM-DD

- [ ] Item *(researched YYYY-MM-DD)*
  - Seller A — $XX.XX, X.X★ — **Best value:** reason
  - Seller B — $XX.XX, X.X★
  - Seller C — $XX.XX, X.X★

## Purchased
```

---

### shopping/preferred-brands.md

```markdown
---
file_type: shopping-list
filed_at: ""
title: Preferred Brands
tags: [shopping, preferences]
---

# Preferred Brands

The agent checks this page before adding any item to a list. When a match is found, it pre-fills the preferred brand automatically.

| Item type | Preferred brand/product | Last purchased | Notes |
|-----------|------------------------|----------------|-------|
```
