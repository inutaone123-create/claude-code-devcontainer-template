# queue/ — YAMLタスクキュー

## 概要

並列エージェント実行時のタスク状態を可視化するためのディレクトリです。
multi-agent-shogun の設計を参考に、YAML ファイルベースでタスクを管理します。

## ファイル構成

```
queue/
├── README.md      # このファイル
└── tasks.yaml     # 現在のセッションのタスク一覧
```

## 使い方

### 1. セッション開始時

`tasks.yaml` のヘッダーを埋め、`tasks:` にタスクを追加します：

```yaml
session:
  id: "2026-03-08-001"
  started_at: "2026-03-08 10:00"
  goal: "タスク依存関係機能を実装する"

tasks:
  - id: "001"
    title: "既存コードの調査"
    assignee: "explorer"
    status: "in_progress"
    blocked_by: []
    result: ""
```

### 2. 依存関係の表現

`blocked_by` に依存するタスクIDを列挙します：

```yaml
- id: "003"
  title: "実装"
  assignee: "implementer"
  status: "waiting"
  blocked_by: ["001", "002"]   # 001と002が完了するまで待機
```

### 3. 完了時

`status: "done"` に更新し、`result` に成果を記録します。

## 設計原則（multi-agent-shogun より）

- **ノンブロッキング**: Shogunはタスク完了を待たず次の命令を受け付ける
- **可視性**: 全タスクの状態がYAMLで一目瞭然
- **依存関係**: `blocked_by` で実行順序を制御
- **記録**: `result` に成果を残してナレッジを蓄積

## gitignore

`tasks.yaml` はセッション固有の作業ファイルのため、`.gitignore` に追加することを推奨します。
テンプレートとして管理したい場合はそのままコミットしてください。
