# 🏯 Claude Code × Dev Container 御陣テンプレート

Claude Code の諸将を召喚し、Dev Container の御城内にてプロジェクトをゼロより自律執行するためのテンプレートにございます。

## この御陣にてできること

- Dev Container の御城（Python / Octave / C++ / C# / Rust）をすぐさま築城
- `AGENT_MASTER_PLAN.md` に作戦を記すだけで、Claude Code が自律出陣
- BDDテスト・クロス検証・ドキュメント作成まで、一貫した戦略にて進軍

## 出陣の儀（使い方）

### 其の一：新たな御城を築く

GitHubの「Use this template」ボタンを押し、新たなリポジトリを開城すること。

### 其の二：軍略書のプレースホルダーを埋める

以下のファイルの `{{...}}` を実際の値に書き改めること：

| 軍略書 | 書き改める箇所 |
|--------|--------------|
| `CLAUDE.md` | Git設定・リモートURL・技術的知見 |
| `AGENT_MASTER_PLAN.md` | 目標・フェーズ設計・制約条件 |
| `.devcontainer/devcontainer.json` | プロジェクト名 |

詳細は `AGENT_EXECUTION_GUIDE.md` のプレースホルダー一覧を参照されたし。

### 其の三：Dev Container の御城を開く

```bash
code .
# F1 → "Dev Containers: Reopen in Container"
# （初陣は御城の築城に数分かかり申す）
```

### 其の四：Claude Code に出陣を命ずる

```bash
claude
```

出陣の号令（コピー&ペーストされたし）：
```
AGENT_MASTER_PLAN.md を読んで、Phase 0 から順番に実行してください。
Dockerfile、docker-compose.yml、.devcontainer/ は変更せず、
CLAUDE.md のルールに従って作業してください。
```

## 御城の見取り図（ファイル構成）

```
.
├── Dockerfile                  # 御城の設計図（5言語 + Claude Code）
├── docker-compose.yml          # 部隊編成
├── .devcontainer/
│   └── devcontainer.json       # 御城設定
├── CLAUDE.md                   # 軍律（作業ルール・ワークフロー）
├── AGENT_MASTER_PLAN.md        # 作戦書（Claude Code への指示書）
├── AGENT_EXECUTION_GUIDE.md    # 出陣手順・プレースホルダー一覧
├── .claude/
│   ├── settings.json           # 兵力設定（デフォルトモデル）
│   └── agents/
│       ├── explorer.md         # 🔍 斥候部隊（Haiku）
│       ├── implementer.md      # ⚙️ 実装部隊（Sonnet）
│       └── architect.md        # 🏛️ 軍師（Opus）
└── .gitignore
```

## 召喚される諸将

作業の重さに応じて、Claude が自動的に適切な将を召喚いたします：

| 将 | モデル | 得意な戦 |
|----|--------|---------|
| 🔍 explorer（斥候） | Haiku | ファイル探索・構造把握・軽い調査 |
| ⚙️ implementer（実装） | Sonnet | 通常の実装・テスト修正・バグ修正 |
| 🏛️ architect（軍師） | Opus | 設計・計画・複雑な技術的意思決定 |

各将は出陣時に名乗りを上げ申す。また `.claude/agent.log` に召喚の記録が残り候。

## 御城に備わる兵器（開発環境）

| 兵器/流派 | 詳細 |
|----------|------|
| Python | 3.x + pytest, behave, numpy, scipy |
| Octave | latest + signal package |
| C++ | g++ + cmake + Eigen |
| C# | .NET SDK 8.0 |
| Rust | latest (cargo) |
| Claude Code | latest (npm) |

## 御法度（ライセンス）

MIT License
