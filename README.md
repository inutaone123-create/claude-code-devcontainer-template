# Claude Code × Dev Container プロジェクトテンプレート

Claude Code エージェントを使って、Dev Container内でプロジェクトをゼロから自律実行するためのテンプレートです。

## このテンプレートでできること

- Dev Container環境（Python / Octave / C++ / C# / Rust）をすぐに起動
- `AGENT_MASTER_PLAN.md` にプロジェクト計画を書くだけで、Claude Codeが自律実行
- BDDテスト・クロス検証・ドキュメント作成まで一貫した手順で進められる

## 使い方

### 1. このテンプレートから新しいリポジトリを作成

GitHubの「Use this template」ボタンをクリック。

### 2. プレースホルダーを埋める

以下のファイルの `{{...}}` を実際の値に置き換えます：

| ファイル | 何を変える |
|----------|-----------|
| `CLAUDE.md` | Git設定・リモートURL・技術的知見 |
| `AGENT_MASTER_PLAN.md` | 目標・フェーズ設計・制約条件 |
| `.devcontainer/devcontainer.json` | プロジェクト名 |

詳細は `AGENT_EXECUTION_GUIDE.md` のプレースホルダー一覧を参照。

### 3. Dev Containerで開く

```bash
code .
# F1 → "Dev Containers: Reopen in Container"
```

### 4. Claude Codeを実行

```bash
claude
```

プロンプト:
```
AGENT_MASTER_PLAN.md を読んで、Phase 0 から順番に実行してください。
Dockerfile、docker-compose.yml、.devcontainer/ は変更せず、
CLAUDE.md のルールに従って作業してください。
```

## ファイル構成

```
.
├── Dockerfile                  # 開発環境（5言語 + Claude Code）
├── docker-compose.yml          # サービス定義
├── .devcontainer/
│   └── devcontainer.json       # Dev Container設定
├── CLAUDE.md                   # プロジェクトルール（作業ルール・ワークフロー）
├── AGENT_MASTER_PLAN.md        # プロジェクト計画（Claude Code への指示書）
├── AGENT_EXECUTION_GUIDE.md    # 実行手順・プレースホルダー一覧
└── .gitignore
```

## 含まれる開発環境

| 言語/ツール | バージョン |
|-------------|-----------|
| Python | 3.x + pytest, behave, numpy, scipy |
| Octave | latest + signal package |
| C++ | g++ + cmake + Eigen |
| C# | .NET SDK 8.0 |
| Rust | latest (cargo) |
| Claude Code | latest (npm) |

## ライセンス

MIT License
