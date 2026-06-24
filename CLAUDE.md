# CLAUDE.md: unb-sat.github.io

The UnB-SAT group website: a multi-page [just-the-docs](https://just-the-docs.com)
site published with GitHub Pages at <https://unb-sat.github.io>.

The data and the generator live in the sibling repo **`UnB-SAT/.github`**
(`data/students.yml` + `scripts/build_profile.py`). See that repo's `CLAUDE.md` for
the full picture. This file covers the website side.

## Generated vs hand-maintained

Do NOT hand-edit content between `<!-- AUTOGEN:* -->` markers; it is overwritten on
the next build:

- `people.md`   ← `PEOPLE` (PI + student grid)
- `theses.md`   ← `ONGOING` (current) + `THESES` (completed)
- `research.md` ← `IC` (Iniciação Científica)

Edit by hand (these are static):

- `index.md` (home, with the logo banner)
- `publications.md` (**new papers go here**)
- `teaching.md` (FLIA)
- `_config.yml`, `assets/` (logo etc.)

## How it updates

- `.github/workflows/build.yml` checks out `UnB-SAT/.github`, runs the generator with
  `UNB_SAT_SITE_DIR=$GITHUB_WORKSPACE`, and commits the regenerated pages. Triggers:
  a daily schedule, manual run (Actions tab), and `repository_dispatch` (type
  `rebuild`) sent by the `.github` repo when its data changes.
- So to change people / theses / IC: edit `data/students.yml` in `UnB-SAT/.github` and
  push there; this site rebuilds itself.
- To build locally: clone both repos side by side and run
  `python3 scripts/build_profile.py` from the `.github` repo (it writes
  `../unb-sat.github.io/...`).

## Conventions (keep these)

- Body text in **English**; **no em dash (`—`)**; few emojis.
- Each page has just-the-docs front matter (`title`, `nav_order`) and, where useful, a
  table of contents:

  ```
  ## Table of contents
  {: .no_toc .text-delta }

  1. TOC
  {:toc}
  ```

- Markdown inside `<details>` needs `markdown="1"` (kramdown does not parse it
  otherwise), e.g. the "Earlier work" block in `publications.md`.
- The site-wide footer (lab-status disclaimer + credit) is `footer_content` in
  `_config.yml`.
- The logo is `assets/logo.png` (the organization avatar), shown as the sidebar logo
  (`logo:` in `_config.yml`) and as a banner in `index.md`.

## GitHub Pages

Settings → Pages → Deploy from a branch → `main` / root. The just-the-docs theme is a
`remote_theme` in `_config.yml`.
