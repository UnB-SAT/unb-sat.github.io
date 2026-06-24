# unb-sat.github.io

Source for the UnB-SAT group website, published with GitHub Pages at
<https://unb-sat.github.io>.

`index.md` is **generated**, do not edit it by hand. It is produced from the
[`UnB-SAT/.github`](https://github.com/UnB-SAT/.github) repository, which holds the
data (`data/students.yml`) and the generator (`scripts/build_profile.py`).

## How it updates

A workflow here, [`.github/workflows/build.yml`](.github/workflows/build.yml), checks
out the `UnB-SAT/.github` repo, runs the generator and commits `index.md`. It runs:

- on a **daily schedule**, and
- **on demand**: Actions tab, "Build site from UnB-SAT/.github", "Run workflow".

So to update the site, edit the data in `UnB-SAT/.github` and push, then run this
workflow (or wait for the daily run). No secrets are required.

To build locally instead, clone both repos side by side and run the generator from
the `.github` repo (it writes `../unb-sat.github.io/index.md`):

```bash
pip install pyyaml
python3 scripts/build_profile.py
```

## GitHub Pages

Settings → Pages → Build and deployment → Deploy from a branch → `main` / root.
The Cayman theme is configured in [`_config.yml`](_config.yml).
