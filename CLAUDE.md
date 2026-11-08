# accounting-guides

Plain-language guides to bookkeeping and business tax for non-accountants, by country and language,
published as a static site at https://books.alphacargo.co.th/. There is no application code: the
content is Markdown in `docs/`, built with MkDocs Material and mkdocs-static-i18n.

[README.md](README.md) describes the layout and local preview. [CONTRIBUTING.md](CONTRIBUTING.md)
gives the steps for adding a page, country or language, and the writing rules. Follow them.

## Content

- `docs/fundamentals/` holds country-neutral accounting ideas. `docs/thailand/` holds Thai law,
  rates, forms and deadlines. Thailand is the only country so far.
- Each of the 21 pages exists in English (`vat.md`), Thai (`vat.th.md`) and Chinese (`vat.zh.md`).
  A change to the meaning of a page applies to all three files.
- The as-of date for figures is on the country landing page, once per language. The Thai page uses
  the Buddhist Era year (22 ตุลาคม 2569 is 22 October 2026). Update all three when figures change.
- The material is educational, not tax or legal advice. Rates and deadlines need a cited source.

## Commands

```sh
python3 -m venv .venv && . .venv/bin/activate
pip install -r requirements.txt
mkdocs serve             # local preview
mkdocs build --strict    # the check the deploy workflow runs
```

`mkdocs build --strict` was run on 2026-11-08 with the pinned requirements under Python 3.12, the
version the workflow uses, and passed. There are no other tests.

## Behaviour of the build

- A broken link between pages fails `mkdocs build --strict`.
- A page missing from `nav:` in `mkdocs.yml` does not fail it. The build reports the page only at
  INFO level and still publishes it, with no navigation entry. Check `nav:` by hand.
- A missing translation does not fail it either: the English page is shown instead
  (`fallback_to_default: true`).
- Only `docs/` is built, so files at the repository root, such as this one, are not published.

## How changes land

The base branch is `main`. Work on a branch and open a pull request against `main`.

`.github/workflows/deploy.yml` runs on every push to `main` and on manual dispatch. It builds the
site and publishes it to GitHub Pages, so every merge is a publication, including merges that change
no page. The workflow does not run on pull requests, so nothing checks a branch before it merges.
Run `mkdocs build --strict` first.
