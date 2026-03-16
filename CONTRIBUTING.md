# Contributing Guide

## Table of contents
- [Branch strategy](#branch-strategy)
- [Branch naming](#branch-naming)
- [Commit messages](#commit-messages)
- [Pull request rules](#pull-request-rules)
- [Code review rules](#code-review-rules)
- [Do not commit](#do-not-commit)

---

## Branch strategy

| Branch | Purpose | Who merges |
|---|---|---|
| `main` | Stable releases only | Team lead via PR |
| `develop` | Integration branch — all features merge here | Team lead via PR |
| `feat/*` | New features | Author opens PR → develop |
| `fix/*` | Bug fixes | Author opens PR → develop |
| `data/*` | Data pipeline work | Author opens PR → develop |
| `exp/*` | Experiments (may be discarded) | Author opens PR → develop |
| `docs/*` | Documentation updates | Author opens PR → develop |

**Never push directly to `main` or `develop`.** Always work on a separate branch and open a Pull Request.

---

## Branch naming

Use lowercase, hyphen-separated, short and descriptive.

```
feat/pca-feature-selector
fix/nan-handling-pipeline
data/sensor-preprocessing
exp/autoencoder-baseline
docs/update-readme-setup
```

---

## Commit messages

Follow [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/).

**Format:** `<type>: <short description>`

| Type | When to use |
|---|---|
| `feat` | Adding a new feature |
| `fix` | Fixing a bug |
| `data` | Adding or modifying data pipeline |
| `refactor` | Restructuring code without changing behavior |
| `test` | Adding or updating tests |
| `docs` | Documentation only |
| `chore` | Config, dependencies, tooling |
| `exp` | Experimental work |

**Examples:**
```
feat: add PCA feature selector module
fix: handle NaN in sensor data preprocessing
data: add raw sensor data loader
refactor: split feature_extractor into submodules
test: add unit tests for normalization utils
docs: update README with pipeline setup instructions
chore: add pre-commit hooks for ruff and black
```

Rules:
- Use **present tense** — "add feature" not "added feature"
- Keep the description **under 72 characters**
- No period at the end

---

## Pull request rules

### Before opening a PR
- [ ] Your branch is up to date with `develop`
- [ ] All tests pass locally (`pytest`)
- [ ] Code is formatted (`black .` and `ruff check .`)
- [ ] No secrets, data files, or model weights are committed
- [ ] PR description clearly explains what changed and why

### PR size
Keep PRs small and focused. One PR = one logical change.
If your branch has grown large, split it into smaller PRs.

### Merging
- All PRs require **at least 1 approval** before merging
- The **author does not merge their own PR** — the reviewer or team lead merges
- Use **Squash and merge** to keep the history clean on `develop`
- Delete the branch after merging

### PR title format
Follow the same Conventional Commits format:
```
feat: add PCA feature selector module
fix: handle NaN in sensor data preprocessing
```

---

## Code review rules

**For reviewers:**
- Review within **24 hours** of being assigned
- Be constructive — suggest, don't demand
- Approve only when you have actually read the code
- Use GitHub's **"Request changes"** if something must be fixed before merging

**For authors:**
- Respond to all comments before requesting re-review
- Do not resolve reviewer comments yourself — let the reviewer resolve
- If you disagree with a comment, discuss it — don't silently ignore it

---

## Do not commit

The following must **never** be committed to the repo:

- Raw or processed data files (`*.csv`, `*.parquet`, `*.pkl`, etc.)
- Model weights (`*.pt`, `*.pth`, `*.onnx`, etc.)
- Secret keys, API tokens, passwords (`.env`, `secrets.yaml`)
- Large binary files of any kind
- Personal IDE config (`.vscode/`, `.idea/`)

If you accidentally committed any of the above, notify the team lead immediately.
