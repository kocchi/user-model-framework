---
name: user-model-core
description: User Model フレームワークの管理スキル。初期化、表示、更新、履歴管理を提供。「user-model を初期化」「プロファイルを見せて」「変更履歴」などで発火。
---

# User Model Core

User Model フレームワークの中核スキル。個人データ（`user_model.yaml`）の管理を支援します。

## 設定

このスキルは `config.yaml` から設定を読み込みます：

```yaml
# ~/.agent/skills/user-model-core/config.yaml
paths:
  user_model: "~/.agent/data/user_model.yaml"
  schema: "~/.agent/schema/user_model_schema.json"
  changelog: "~/.agent/data/CHANGELOG.md"
  template: "~/.agent/templates/user_model.template.yaml"
```

## コマンド

### 初期化 (`init`)

新規ユーザー向け。テンプレートから `user_model.yaml` を作成。

```
「user-model を初期化して」
「User Model をセットアップ」
```

**手順:**
1. `config.yaml` からパスを読み込む
2. テンプレートを `data/user_model.yaml` にコピー
3. 基本情報（名前、タイムゾーン）を対話で入力
4. CHANGELOG.md を初期化

### 表示 (`view`)

現在の User Model を表示。

```
「私のプロファイルを見せて」
「user-model の内容を表示」
```

**出力形式:**
- セクション別に要約表示
- 詳細は「詳しく」で展開

### 更新 (`update`)

セクションを更新。必ず diff 表示 → 確認 → 保存。

```
「stable を更新したい」
「mutable.current_projects を追加」
```

**手順:**
1. 対象セクションを特定
2. 現在値を表示
3. 変更案を diff 形式で提示
4. 確認後に保存
5. CHANGELOG.md に追記

### 履歴 (`history`)

変更履歴を表示。

```
「変更履歴を見せて」
「いつ何を変更した？」
```

### 検証 (`validate`)

スキーマに対して検証。

```
「user-model を検証して」
「YAML が壊れてないか確認」
```

## 他のユーザーへの配布

このフレームワークを他の人が使う場合：

1. `templates/` からテンプレートをコピー
2. `config.yaml` でパスをカスタマイズ
3. `init` コマンドで初期化
4. 自分用にカスタマイズ

## ファイル構成

```
~/.agent/
├── skills/user-model-core/
│   ├── SKILL.md          # このファイル
│   └── config.yaml       # パス設定
├── templates/            # 配布用テンプレート
│   ├── user_model.template.yaml
│   └── user_model_schema.json
├── schema/               # 検証用スキーマ
│   └── user_model_schema.json
└── data/                 # 個人データ（gitignore推奨）
    ├── user_model.yaml
    └── CHANGELOG.md
```

## 注意

- `data/` は個人データ。公開リポジトリには含めない
- 更新時は必ず CHANGELOG に記録
- 定期的に `validate` でスキーマ検証
