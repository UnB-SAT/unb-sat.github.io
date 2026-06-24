# CLAUDE.md: unb-sat.github.io

The UnB-SAT group website **and** the single source of truth for the group's people
and advised work. Multi-page [just-the-docs](https://just-the-docs.com) site on GitHub
Pages at <https://unb-sat.github.io>. It builds itself (no cross-repo steps).

## Source of truth and generation

- `data/students.yml` is the only place to edit people and advised work (field docs at
  the top of that file).
- `scripts/build_profile.py` rewrites the content between `<!-- AUTOGEN:* -->` markers.
  It globs `*.md` in the repo root and fills each page's declared markers:
  - `PEOPLE` -> `people.md` (PI card + student grid)
  - `ONGOING` + `THESES` -> `theses.md` (current, then completed)
  - `IC` -> `research.md` (Iniciação Científica)
- Static pages, edit by hand: `index.md` (home + logo banner), `publications.md`,
  `teaching.md`. New publications go in `publications.md`, newest-first within each
  section.

## Update flow

1. Edit `data/students.yml`. Use `status: ongoing` for work in progress; IC entries
   set `program: PIBIC` or `PIBITI`. Theme is `sat | planning | moj | ai`.
2. `pip install pyyaml` (once), then `python3 scripts/build_profile.py`.
3. Commit `data/students.yml` and the regenerated pages, then push.

`.github/workflows/build.yml` also rebuilds on any push that changes `data/` or
`scripts/` (and on demand). It triggers only on those paths, so the bot's page commit
never re-triggers it. Verify sync: `python3 scripts/build_profile.py --check`.

## The other repo

<https://github.com/UnB-SAT/.github> is the **static** organization profile (PI card
plus a link to this site). It has no data or generator; if the PI card or the site
link changes, update it there by hand.

## Conventions (keep these)

- Body text in English; **no em dash (`—`)**; few emojis.
- Pages use just-the-docs front matter (`title`, `nav_order`) and, where useful, a
  `{:toc}` block (`## Table of contents` + `{: .no_toc .text-delta }` + `1. TOC` +
  `{:toc}`).
- Markdown inside `<details>` needs `markdown="1"` (kramdown does not parse it
  otherwise), e.g. the "Earlier work" block in `publications.md`.
- Avatars are square (`github` handle -> real avatar, empty -> ui-avatars initials).
  Confirm a handle exists: `curl -sI https://github.com/<handle>.png`.
- `_config.yml` excludes `CLAUDE.md`, `README.md`, `data/` and `scripts/` from the
  build, and sets the footer disclaimer (`footer_content`) and the sidebar `logo`.

## Data sources (when adding entries)

- TCCs: BDM, `https://bdm.unb.br/browse?type=advisor&value=Ribas%2C+Bruno+C%C3%A9sar`
  (incomplete TLS chain; fetch with `curl -k`).
- M.Sc.: `https://repositorio.unb.br/browse?type=advisor&value=Ribas%2C+Bruno+C%C3%A9sar`.
- Publications: DBLP `https://dblp.org/pid/121/4222` (Scholar and ResearchGate block
  scraping). Lattes XML at `/home/ribas/UnB-SAT/lattes.xml` (ISO-8859-1) lists IC/PIBIC
  advisings and Brazilian-venue papers.
