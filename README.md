# Accounting Guides

Plain-language guides to bookkeeping and business tax for non-accountants, organised by country and language.

**Site:** https://ituoo.com/accounting-guides/

| Section | Languages |
| --- | --- |
| Accounting fundamentals (country-neutral) | English, ภาษาไทย, 中文 |
| Thailand | English, ภาษาไทย, 中文 |

Built with [MkDocs Material](https://squidfunk.github.io/mkdocs-material/) and [mkdocs-static-i18n](https://github.com/ultrabug/mkdocs-static-i18n). Every push to `main` is built and published to GitHub Pages by `.github/workflows/deploy.yml`.

## Layout

```
docs/
  index.md                    # home page (index.th.md, index.zh.md = translations)
  fundamentals/               # country-neutral accounting basics
    accounting-equation.md
    accounting-equation.th.md
    accounting-equation.zh.md
  thailand/                   # one folder per country
    index.md                  # country landing page
    vat.md  vat.th.md  vat.zh.md
mkdocs.yml                    # navigation, languages, theme
```

A translation lives next to the English page with a language suffix (`vat.th.md`). If a translation is missing, the English page is shown instead.

## Preview locally

```sh
python3 -m venv .venv && . .venv/bin/activate
pip install -r requirements.txt
mkdocs serve
```

See [CONTRIBUTING.md](CONTRIBUTING.md) to add a country, a language or a page.

## Disclaimer

Educational material only, not tax or legal advice. Figures are dated on each country's landing page; confirm current rules with the tax authority or a licensed accountant.
