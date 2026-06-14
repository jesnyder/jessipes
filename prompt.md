# GoodEats — Project Objective & AI Guidance

## Project Goal

This repository organizes cooking recipes, kitchen techniques, and nutritional information into a browsable, well-structured reference. The end result is a website where `docs/index.html` serves as a landing page with clickable links to individual pages covering specific topics (e.g., tofu preparation, paneer marinating and cooking).

## Site Structure

```
goodEats/
├── prompt.md                        # This file — project objective and AI guidance
├── docs/
│   ├── index.html                   # Landing page: recipe links + nutritional summary
│   ├── marinating-tofu.html         # Tofu prep, marinade, cooking, nutrition
│   └── marinating-paneer.html       # Paneer marinade, cooking methods, nutrition
├── recipes/
│   ├── marinating-tofu.md           # Markdown source for tofu page
│   └── marinating-paneer.md         # Markdown source for paneer page
└── user_provided/
    └── dietary_restrictions.csv     # User dietary preferences — always read before writing content
```

## Dietary & Preference Context

Always check `user_provided/dietary_restrictions.csv` before writing recipes or techniques. Current guidance:
- Vegetarian
- Light on cheese
- High protein is a priority — prefer preparations and ingredients that maximize protein density
- Equipment available: oven, stove, Instant Pot
- Enjoys: beans, tomatoes, vegetables

## Guidance for Future AI Assistance

1. **Always consult `user_provided/` first.** Before drafting or updating any recipe or technique, read the dietary restrictions file and apply the guidance throughout.

2. **Freeze-then-thaw tofu is the recommended default.** Given the high-protein priority, this prep step is not optional — it increases protein density and improves marinade absorption.

3. **Keep markdown and HTML in sync.** Source content lives in `recipes/*.md`. When updating content, update both the `.md` source and the corresponding `docs/<topic>.html` page.

4. **Index page is a navigation hub.** `docs/index.html` links to every topic page and includes a nutritional summary table. When a new recipe or technique page is added:
   - Add a card link in the "Recipes & Techniques" grid on the index
   - Add a row to the nutritional overview table on the index

5. **One topic per HTML page.** Each cooking technique or recipe category gets its own file in `recipes/` and its own page in `docs/`.

6. **Nutritional information belongs on every page.** Include a nutritional table at the bottom of each `docs/*.html` page, and a summary callout on the index.

7. **Consistent visual style.** Follow the styling established in `docs/index.html` — warm tones, Georgia serif font, `.recipe-box`, `.tip`, and `.nutrition-box` CSS classes.

8. **Back navigation.** Every topic page should include a `← Back to GoodEats` link at the top pointing to `index.html`.
