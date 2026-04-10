[English](README.md) | 日本語

# プロジェクトテンプレート

このリポジトリは、新規プロジェクト本体と private な development-docs リポジトリを初期化するためのブートストラップである。
実際の開発を始める前に、governance level を必ず1つだけ選び、初期化手順を実行する。

## ブートストラップ状態

初期化前の root には、次だけが存在する前提とする。

- `.gitignore`
- `README.md`
- `README.ja.md`
- `governance/`

`CLAUDE.md`、`AGENT.md`、`development-docs/` は初期化後に生成される。

## 利用可能なプロファイル

- `governance/light/`: 低儀式の project-root / development-docs テンプレート
- `governance/strict/`: 高規律の project-root / development-docs テンプレート

## 初期化

初期化の流れは次のとおり。

1. governance level を選ぶ
2. `governance/<level>/project-root/.` を main repository root に展開する
3. `<project-name>-development-docs` という private repository を作成する
4. `governance/<level>/development-docs/` の内容でその repository を初期化する
5. それを `development-docs/` という名前で clone して戻す
6. `governance/` を削除する

## コマンド例

以下を main repository root で実行する。

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

## 初期化後

main repository には少なくとも次が存在する状態になる。

- `README.md`
- `README.ja.md`
- `CLAUDE.md`
- `AGENT.md`
- `development-docs/`

main repository 側の AI 入口ファイルは、次を参照する前提にする。

1. `development-docs/rules/AI_RUNTIME_RULES.md`
2. `development-docs/AI_KNOWLEDGE.md`
3. `README.md`

その上で、両方の repository 内の placeholder を実プロジェクトに合わせて書き換える。

ディレクトリセットアップ後の first action は、
`development-docs/rules/language-policy.md` にプロジェクトの言語設定を定義すること。
