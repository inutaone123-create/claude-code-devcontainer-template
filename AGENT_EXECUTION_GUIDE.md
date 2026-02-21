# AGENT EXECUTION GUIDE
# Dev Container環境でのClaude Code実行手順

---

## 🎬 使い方（毎回同じ手順）

### ステップ1: 初期設定ファイルを確認

このテンプレートには以下が含まれています：

- `Dockerfile` — 開発環境（Python/Octave/C++/C#/Rust + Claude Code）
- `docker-compose.yml` — サービス定義
- `.devcontainer/devcontainer.json` — Dev Container設定

**プロジェクト開始前に `{{...}}` のプレースホルダーを埋めてください：**
- `.devcontainer/devcontainer.json` の `"name"` フィールド
- `CLAUDE.md` の Git設定・リモートURL・技術的知見
- `AGENT_MASTER_PLAN.md` の目標・フェーズ・制約条件

### ステップ2: Dev Containerで開く

```bash
# VSCodeでフォルダを開く
code .

# F1 → "Dev Containers: Reopen in Container"
# （初回はDockerイメージのビルドに数分かかります）
```

### ステップ3: Dev Container内でClaude Codeを実行

```bash
# VSCode内蔵ターミナル（既にコンテナ内）
claude
```

**Claude Codeへのプロンプト（コピー&ペースト）**:

```
Dev Container内で作業中です。

AGENT_MASTER_PLAN.md を読んで、Phase 0 から順番に実行してください。

Dockerfile、docker-compose.yml、.devcontainer/ は既に存在するので、
それらは変更せず、他のファイルを作成・編集してください。

CLAUDE.md のルールに従って作業してください。
```

---

## 🐳 Dockerファイル詳細

### Dockerfile に含まれるツール

| カテゴリ | ツール | 用途 |
|----------|--------|------|
| 言語 | Python 3, pip | スクリプト・テスト |
| 言語 | Octave + signal pkg | 数値計算 |
| 言語 | C++ (g++, cmake) | 高速実装 |
| 言語 | .NET SDK 8.0 | C# 実装 |
| 言語 | Rust (cargo) | 安全性重視実装 |
| AI | Claude Code (npm) | エージェント実行 |
| テスト | pytest, behave | Python テスト・BDD |
| 品質 | black | コードフォーマット |

### 言語を追加・削除したい場合

`Dockerfile` の該当 `RUN apt-get install` / `RUN pip3 install` 行を編集し、
`docker-compose.yml` の `build` 後にコンテナを再ビルドしてください：

```bash
docker-compose build
# F1 → "Dev Containers: Rebuild Container"
```

---

## 📁 テンプレートのプレースホルダー一覧

プロジェクト開始時に以下を置換してください：

| プレースホルダー | 説明 | 例 |
|-----------------|------|----|
| `{{PROJECT_NAME}}` | リポジトリ名 | `my-awesome-project` |
| `{{PROJECT_TITLE}}` | プロジェクト表示名 | `My Awesome Project` |
| `{{GIT_USER_NAME}}` | Gitユーザー名 | `YourName` |
| `{{GIT_USER_EMAIL}}` | Gitメールアドレス | `you@example.com` |
| `{{GITHUB_REMOTE}}` | GitHubリモートURL | `https://github.com/user/repo` |
| `{{LICENSE}}` | ライセンス名 | `MIT`, `CC BY 4.0`, `Apache 2.0` |
| `{{YEAR}}` | 実装年 | `2025` |
| `{{LICENSE_ATTRIBUTION}}` | 帰属表示（元ソースがある場合） | `Based on XXX by YYY` |
| `{{DELIVERABLE_N}}` | 最終成果物 | `Python実装`, `クロス検証` |
| `{{IMPL_PHASE_N}}` | 実装フェーズ名 | `Python実装（リファレンス）` |
| `{{CONSTRAINT_N}}` | 制約条件 | `FFT正規化: Forward=なし, Inverse=1/N` |
| `{{VALIDATION_CRITERIA}}` | 検証合格基準 | `全ペア 相対誤差 < 1e-10` |
| `{{LANG_N}}` | 言語名（技術的知見） | `Python`, `C++` |

---

## ✅ プロジェクト開始チェックリスト

- [ ] このテンプレートリポジトリから新しいリポジトリを作成した
- [ ] `{{...}}` プレースホルダーをすべて埋めた
- [ ] `AGENT_MASTER_PLAN.md` のフェーズ設計を完了した
- [ ] `CLAUDE.md` のGit設定・リモートURLを設定した
- [ ] Dev Container でビルドが成功した
- [ ] `claude` コマンドが起動できることを確認した
- [ ] Claude Code にプロンプトを渡して実行開始した
