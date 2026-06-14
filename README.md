# GoodEats — Project Objective & AI Guidance

## Project Goal

This repository organizes cooking recipes, kitchen techniques, and nutritional information into a browsable, well-structured reference. The end result is a website where `docs/index.html` serves as a landing page with clickable links to individual pages covering specific topics (e.g., tofu preparation, paneer marinating and cooking).

## Site Structure

```
goodEats/
├── README.md                        # This file — project objective and AI guidance
├── docs/
│   ├── index.html                   # Landing page: recipe links (single column) + nutritional summary table (sortable by protein)
│   ├── marinating-tofu.html         # Tofu prep, marinade, cooking, nutrition
│   ├── marinating-paneer.html       # Paneer marinade options (incl. Labneh & Miso), cooking methods, nutrition
│   ├── preparing-beets.html         # Beet prep: boiled, steamed, roasted, grilled, pressure cooked, raw — with nutritional tradeoffs table
│   └── ingredients.html             # Pantry reference table — all ingredients with nutritional info, culinary role, stock status; filterable and sortable
├── recipes/
│   ├── marinating-tofu.md           # Markdown source for tofu page
│   └── marinating-paneer.md         # Markdown source for paneer page
└── user_provided/
    ├── dietary_restrictions.csv     # User dietary preferences — always read before writing content
    ├── ingredients.csv              # Pantry inventory — in stock and out of stock ingredients
    └── morningSmoothie.csv          # Morning smoothie reference
```

## Dietary & Preference Context

Always check `user_provided/dietary_restrictions.csv` before writing recipes or techniques. Current guidance:
- Vegetarian
- Light on cheese
- High protein is a priority — prefer preparations and ingredients that maximize protein density
- Equipment available: oven, stove, Instant Pot
- Enjoys: beans, tomatoes, vegetables

## Guidance for Future AI Assistance

1. **Always consult `user_provided/` first.** Before drafting or updating any recipe or technique, read the dietary restrictions file and the ingredients inventory. Apply dietary guidance throughout and prefer in-stock ingredients when suggesting recipes.

2. **Freeze-then-thaw tofu is the recommended default.** Given the high-protein priority, this prep step is not optional — it increases protein density and improves marinade absorption.

3. **Keep markdown and HTML in sync.** Source content lives in `recipes/*.md`. When updating content, update both the `.md` source and the corresponding `docs/<topic>.html` page.

4. **Index page is a navigation hub.** `docs/index.html` links to every topic page and includes a nutritional summary table. When a new recipe or technique page is added:
   - Add a card link in the "Recipes & Techniques" list on the index (single column layout)
   - Add a row to the nutritional overview table on the index

5. **One topic per HTML page.** Each cooking technique or recipe category gets its own file in `recipes/` and its own page in `docs/`.

6. **Nutritional information belongs on every page.** Include a nutritional table at the bottom of each `docs/*.html` page, and a summary callout on the index.

7. **Consistent visual style.** Follow the styling established in `docs/index.html` — warm tones (`#faf9f6` background, `#c8a96e` gold accent, `#f0e8d8` fills), Georgia serif font, `.recipe-box`, `.tip`, and `.nutrition-box` CSS classes.

8. **Back navigation.** Every topic page should include a `← Back to GoodEats` link at the top pointing to `index.html`.

9. **Sortable tables.** Tables with quantitative columns (protein, calories) should be click-sortable. Follow the pattern in `docs/index.html` and `docs/ingredients.html` — inline JS at the bottom, `th.sortable` class with `::after` arrow indicators.

10. **Ingredients page is the pantry reference.** When new ingredients appear in `user_provided/ingredients.csv`, add them to `docs/ingredients.html` with nutritional info, culinary role tags, and stock status. Roles to use: Acid, Aromatic / Spice, Fat / Richness, Fermented / Probiotic, Protein base, Sweet / Starchy, Umami, Vegetable.
