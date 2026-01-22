# User Model Framework

> Make AI agents understand you better

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-Compatible-green.svg)](https://agentskills.io)

AI エージェントがあなたを理解するためのフレームワーク。  
価値観、思考スタイル、コミュニケーション方法を定義し、パーソナライズされた対話を実現します。

## Features

- 🧬 **Self-evolving** - 会話から学習し、設定を自動更新提案
- 📋 **Structured Profile** - 安定（価値観）/ 可変（プロジェクト）/ 学習ログの3層構造
- 🔄 **Cross-platform** - Claude Code / Cursor 両対応
- 📦 **Plugin Ready** - Claude Code Plugin として簡単導入

## Quick Start

### 1. Plugin インストール

```bash
/plugin marketplace add kocchi/user-model-framework
/plugin install user-model-framework
```

### 2. User Model 初期化

```bash
# テンプレートをコピー
mkdir -p ~/.agent/data
cp ~/.claude/plugins/user-model-framework/templates/user_model.template.yaml \
   ~/.agent/data/user_model.yaml

# または Agent に依頼
# 「user-model を初期化して」
```

### 3. 使い始める

```
「私のことを教えて」
「価値観を追加したい」
「進化して」
```

## User Model Structure

```yaml
user_model.yaml:
  stable:                    # 長期安定（価値観、思考スタイル）
    north_star:              # 目標、成功定義、守るもの、避けるもの
    decision_engine:         # 価値観、品質基準、トレードオフ
    thinking_os:             # メンタルモデル、協働スタイル
    communication_prefs:     # 言語、トーン、フォーマット

  mutable:                   # 短期可変（現在のコンテキスト）
    current_roles: []
    current_projects: []
    constraints_now: {}

  learning_log:              # 学習記録
    corrections_that_worked: []
    common_pitfalls: []

  agent_runtime_policy:      # Agent の振る舞い設定
```

## Skills

| Skill | Description | Trigger |
|-------|-------------|---------|
| `user-model-core` | 初期化、表示、検証 | 「user-model を初期化」「プロファイル表示」 |
| `user-model-evolve` | 会話から学習し更新提案 | 「進化して」「学習して」 |
| `user-model-update-stable` | stable セクション更新 | 「価値観を追加」 |
| `user-model-update-mutable` | mutable セクション更新 | 「プロジェクトを追加」 |
| `user-model-log-learning` | 学習ログ記録 | 「これは効いた」 |
| `agent-memory-remember` | プロジェクト情報を記憶 | 「記憶して」 |
| `agent-memory-recall` | 記憶を想起 | 「思い出して」 |
| `agent-memory-forget` | 記憶を削除 | 「忘れて」 |

## Self-Evolution

Agent は会話中に以下を検知し、`user_model.yaml` の更新を提案します：

```
🧬 進化の提案

今回の会話から以下の学習を検知しました：

【stable への追加】
A. formatting.prefer に「選択肢は記号で」を追加
   理由: 明示的に要望があった

適用: [A] [全部] [なし]
```

## File Structure

```
user-model-framework/
├── .claude-plugin/
│   └── plugin.json          # Plugin manifest
├── skills/
│   ├── user-model-core/     # 管理統合スキル
│   ├── user-model-evolve/   # 自己進化
│   ├── user-model-update-*/ # セクション更新
│   ├── user-model-log-learning/
│   └── agent-memory-*/      # プロジェクト記憶
├── rules/
│   ├── user-model.md        # Claude Code 用
│   └── user-model.mdc       # Cursor 用
├── templates/
│   ├── user_model.template.yaml
│   └── user_model_schema.json
└── schema/
    └── user_model_schema.json
```

## Configuration

`skills/user-model-core/config.yaml` でパスをカスタマイズ可能：

```yaml
paths:
  user_model: "~/.agent/data/user_model.yaml"
  schema: "~/.agent/schema/user_model_schema.json"
```

## Compatibility

| Tool | Support |
|------|---------|
| Claude Code | ✅ Full (Plugin / Skills / Rules) |
| Cursor | ✅ Full (Skills / Rules) |
| Claude.ai | ⚠️ Skills only (manual upload) |

## Personal Data

このプラグインは **フレームワークのみ** を提供します。  
個人データ（`user_model.yaml`）はプラグイン外で管理してください：

```
~/.agent/data/
├── user_model.yaml      # あなたの個人データ
└── CHANGELOG.md         # 変更履歴
```

推奨: [chezmoi](https://chezmoi.io) でマシン間同期

## Contributing

Contributions welcome! Please open an issue or PR.

## License

MIT License - see [LICENSE](LICENSE) for details.

## Acknowledgments

- [Agent Skills](https://agentskills.io) - Open standard for agent capabilities
- [Anthropic](https://anthropic.com) - Claude and Agent Skills specification
