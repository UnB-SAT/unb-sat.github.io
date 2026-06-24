# unb-sat.github.io

Source for the UnB-SAT group website, published with GitHub Pages at
<https://unb-sat.github.io>.

`index.md` is **generated**, do not edit it by hand. It is produced from the
[`UnB-SAT/.github`](https://github.com/UnB-SAT/.github) repository, which holds the
data (`data/students.yml`) and the generator (`scripts/build_profile.py`).

## Updating

Clone both repositories side by side:

```
UnB-SAT/
├── .github/              # data + generator (this is "dot-github" locally)
└── unb-sat.github.io/    # this repo
```

Then, from the `.github` repo:

```bash
pip install pyyaml
python3 scripts/build_profile.py
```

The generator writes `../unb-sat.github.io/index.md` (this site) and the slim
`profile/README.md` (the organization profile). Commit and push both repositories.

## GitHub Pages

Settings → Pages → Build and deployment → Deploy from a branch → `main` / root.
The Cayman theme is configured in [`_config.yml`](_config.yml).
