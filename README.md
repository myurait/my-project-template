English | [日本語](README.ja.md)

# Project Template

This repository bootstraps a new project and its private development-docs repository.
Before real project work begins, choose exactly one governance level and run the initialization procedure.

## Bootstrap State

Before initialization, root should contain only:

- `.gitignore`
- `README.md`
- `README.ja.md`
- `governance/`

`CLAUDE.md`, `AGENT.md`, and `development-docs/` are created only after initialization.

## Available Profiles

- `governance/light/`: low-ceremony project root and development-docs templates
- `governance/strict/`: high-discipline project root and development-docs templates

## Initialization

The initialization flow is:

1. Choose a governance level.
2. Copy `governance/<level>/project-root/.` into the main repository root.
3. Create a private repository named `<project-name>-development-docs`.
4. Populate that repository from `governance/<level>/development-docs/`.
5. Clone it back into the main repository as `development-docs/`.
6. Remove `governance/`.

## Example Commands

Run the following from the main repository root after setting the variables:

```bash
PROJECT_NAME="my-project"
GITHUB_OWNER="your-org-or-user"
LEVEL="strict"   # light or strict
DOCS_REPO="${PROJECT_NAME}-development-docs"
TMP_DIR="$(mktemp -d)"

cp -R "governance/${LEVEL}/project-root/." ./
cp -R "governance/${LEVEL}/development-docs/." "$TMP_DIR"/

(
  cd "$TMP_DIR"
  git init -b main
  git add .
  git commit -m "Initialize development docs"
  gh repo create "${GITHUB_OWNER}/${DOCS_REPO}" --private --source=. --remote=origin --push
)

gh repo clone "${GITHUB_OWNER}/${DOCS_REPO}" development-docs

rm -rf governance
rm -rf "$TMP_DIR"
```

## After Initialization

The main repository should now contain:

- `README.md`
- `README.ja.md`
- `CLAUDE.md`
- `AGENT.md`
- `development-docs/`

The AI entry files in the main repository should direct agents to:

1. `development-docs/AI_KNOWLEDGE.md`
2. `development-docs/INDEX.md`

Then rewrite the placeholders in both repositories to match the actual project.

The first action after directory setup is to define the development language,
documentation language, and commit message language in
`development-docs/design/01-project-charter.md`.
