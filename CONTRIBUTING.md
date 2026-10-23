# Contributing

## Add a page to an existing country

1. Create `docs/<country>/<topic>.md` in English, starting with one `# Title`.
2. Add translations beside it: `<topic>.th.md`, `<topic>.zh.md`, and so on.
3. Add `<country>/<topic>.md` to the country's list under `nav:` in `mkdocs.yml`, and link it from `docs/<country>/index.md` (and its translations).

## Add a country

1. Create `docs/<country>/index.md`: a short landing page with the as-of date, a disclaimer and links to every page.
2. Add the topic pages. Keep general accounting ideas in `docs/fundamentals/`; put only local law, rates, forms and deadlines in the country folder.
3. Add the country under `Countries:` in `mkdocs.yml`, add its name to each language's `nav_translations`, and add a row to the table in `docs/index.md` (and its translations).

## Add a language

1. Add the locale under `plugins: i18n: languages:` in `mkdocs.yml`, with `nav_translations` for the section names (Home, Accounting fundamentals, Countries, each country).
2. Translate pages by adding files with that suffix, for example `vat.vi.md`. Untranslated pages fall back to English.

## Writing rules

- Link to other pages by their English filename (`vat.md`, `../fundamentals/accounting-equation.md`). The i18n plugin points the link at the reader's language.
- When the same anchor must work in every language, give the heading an explicit id: `## Heading {#stable-id}`.
- Write formulas as display math between `$$` lines.
- Cite sources for rates and deadlines, and update the as-of date on the country landing page when figures change.
- Run `mkdocs build --strict` before pushing; the deploy workflow fails on broken links.
