# unb-sat.github.io

Source for the UnB-SAT group website: a multi-page
[just-the-docs](https://just-the-docs.com) site on GitHub Pages at
<https://unb-sat.github.io>. This repository is also the **single source of truth**
for the group's people and advised work, and it builds itself.

## Layout

```
data/students.yml          people and advised work (edit this)
scripts/build_profile.py   fills the AUTOGEN markers in the pages below
people.md                  generated: PEOPLE
theses.md                  generated: ONGOING + THESES
research.md                generated: IC
index.md                   static: home (logo, about, research lines, links)
publications.md            static: publications (edit by hand, newest-first)
teaching.md                static: FLIA
_config.yml, assets/       theme, logo, site config
```

## Updating

```bash
pip install pyyaml          # once
python3 scripts/build_profile.py
# commit data/students.yml and the regenerated pages, then push
```

A push that changes `data/` or `scripts/` also triggers
[`.github/workflows/build.yml`](.github/workflows/build.yml), which regenerates the
pages and commits them. It triggers only on those paths (not on the generated pages),
so the bot's commit never loops. You can also run it from the Actions tab. Check sync
locally with `python3 scripts/build_profile.py --check`.

## GitHub Pages

Settings → Pages → Deploy from a branch → `main` / root. The theme is the
just-the-docs `remote_theme` in `_config.yml`. `CLAUDE.md`, `README.md`, `data/` and
`scripts/` are excluded from the published site.

## The other repo

[`UnB-SAT/.github`](https://github.com/UnB-SAT/.github) is the static organization
profile (PI plus a link to this site). It has no data or generator.
