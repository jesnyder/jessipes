# GoodEats — Project Objective & AI Guidance

## Project Goal

This repository organizes cooking recipes, kitchen techniques, and nutritional information into a browsable, well-structured reference. The end result is a website where `docs/index.html` serves as a landing page with clickable links to individual pages covering specific topics (e.g., tofu preparation, paneer marinating and cooking).

## Site Structure

```
goodEats/
├── docs/
│   ├── README.md                    # This file — project objective and AI guidance
│   ├── style.css                    # Shared stylesheet for index.html (warm palette, card grid, table, sortable headers)
│   ├── index.html                   # Landing page: recipe links (single column) + nutritional summary table (sortable by protein)
│   ├── marinating-tofu.html         # Tofu prep, marinade, cooking, nutrition
│   ├── marinating-paneer.html       # Paneer marinade options (incl. Labneh & Miso), cooking methods, nutrition
│   ├── preparing-beets.html         # Beet prep: boiled, steamed, roasted, grilled, pressure cooked, raw — with nutritional tradeoffs table
│   ├── cucumber-salad.html          # Cold Asian smashed-cucumber salad with Szechuan peppercorn oil option; pairs with mushroom rice
│   ├── morning-smoothie.html        # Daily 1L smoothie — ingredients (incl. rose hips powder), method, per-ingredient nutrition, iron gap warning, B12/D notes
│   ├── mushroom-rice.html           # Maitake mushroom rice (Instant Pot); UV-B ergosterol → vitamin D2; serves as side to cucumber salad
│   ├── ingredients.html             # Pantry reference table — all ingredients with USDA FDC hyperlinks, nutritional info, culinary role, stock status; filterable and sortable
│   ├── nutritional-guide.html       # Peer-reviewed guide to balanced diet and fasting — cited research with DOI links, sortable nutrient-by-function reference table
│   └── about.html                   # Site philosophy, dietary approach (vegetarian, no seafood, low iron, cycling commuter), kitchen setup, evidence standards
├── recipes/
│   ├── marinating-tofu.md           # Markdown source for tofu page
│   └── marinating-paneer.md         # Markdown source for paneer page
├── user_provided/
│   ├── dietary_restrictions.csv     # User dietary preferences — always read before writing content
│   ├── ingredients.csv              # Pantry inventory — in stock and out of stock ingredients
│   └── morningSmoothie.csv          # Morning smoothie reference
└── usda_api/
    └── api_cred.txt                 # USDA FoodData Central API key — do not commit; see rate limit rule below
```

## Dietary & Preference Context

Always check `user_provided/dietary_restrictions.csv` before writing recipes or techniques. Current guidance:
- **Vegetarian. No seafood.** When listing foods as "not available," say "No (seafood — excluded)" rather than "not vegetarian" — the distinction matters.
- Light on cheese
- High protein is a priority — prefer preparations and ingredients that maximize protein density
- **Iron is a personal health priority.** History of low iron; vegetarian diet means only non-heme iron (2–20% absorption); daily cycling increases oxygen/hemoglobin demand. Flag iron content, absorption enhancers (vitamin C), and inhibitors (tannins, calcium, phytates) throughout. Recommend pairing iron-rich foods with vitamin C and separating from tea/dairy.
- **Cycling commuter — higher energy and endurance nutrition needs.** Carbohydrates are performance fuel, not something to minimize. Electrolyte, glycogen replenishment, and recovery are relevant. Beets (dietary nitrate → endurance) are especially relevant.
- Equipment available: oven, stove, Instant Pot
- Enjoys: beans, tomatoes, vegetables
- User is a scientist — values cause-and-effect explanations, evidence quality, and honesty about uncertainty. State confidence levels. Do not hallucinate.

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

10. **Ingredients page is the pantry reference.** When new ingredients appear in `user_provided/ingredients.csv`, add them to `docs/ingredients.html` with nutritional info, culinary role tags, and stock status. Roles to use: Acid, Aromatic / Spice, Carbohydrate, Fat / Richness, Fermented / Probiotic, Protein base, Sweet / Starchy, Umami, Vegetable. Functional mushroom powders (lion's mane, turkey tail) use Umami. Supplements without food calories (creatine) use Protein base. Psyllium husk and similar fiber supplements use Carbohydrate.

11. **USDA FoodData Central is the nutritional reference standard.** When citing nutritional values, use [USDA FDC](https://fdc.nal.usda.gov/). Hyperlink ingredient names in nutritional tables to their FDC food-details page, opening in a new tab: `<a href="https://fdc.nal.usda.gov/food-details/{FDC_ID}/nutrients" target="_blank" rel="noopener">Name</a>`. Use the USDA API to look up FDC IDs: key is in `usda_api/api_cred.txt`. **Rate limit: wait 10 seconds between API calls.** The following ingredients have no confirmed USDA FDC match and are left unlinked: Szechuan peppercorns, Za'atar, Labneh, Lion's mane powder, Arborio rice, Mexican-style rice, Plum vinegar (ume), Noodles.

12. **Link evidence claims to credible sources.** The user is a scientist and values cause-and-effect reasoning. When stating that a cooking technique or ingredient has a specific effect (nutritional, biochemical, culinary), link to a credible primary or institutional source (USDA, NIH, peer-reviewed journal, university extension). Do not state uncertain claims as facts. State confidence level and note unknowns explicitly.

13. **Labneh cooking behavior.** Labneh is a soft strained-yogurt cheese with high moisture content. It does **not** char at high heat. At high heat, the coating may brown gently, but a crisp crust does not form from labneh itself. Any charring in a labneh-marinated dish comes from the protein underneath (paneer, tofu). Cook labneh-coated dishes on medium-high heat, not maximum heat. Do not describe labneh as "charring well" anywhere in the site.
