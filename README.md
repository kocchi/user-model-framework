# User Model Framework

> Make AI agents understand you deeply — beyond what you consciously know about yourself

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-Compatible-green.svg)](https://agentskills.io)

AI エージェントがあなたを**誰よりも深く**理解するためのフレームワーク。  
表層的な好みだけでなく、メンタルモデル、認知パターン、さらには本人すら自覚しにくい深層構造まで捉えます。

## Features

- 🔬 **Deep Self Analysis** - 7層の深層自己構造分析（顕在〜ライフスクリプト）
- 🧬 **Self-evolving** - 会話から学習し、仮説検証ループで深層理解を構築
- 📋 **Structured Profile** - 安定 / 可変 / 学習ログ / 深層構造の多層構造
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
    thinking_os:             # メンタルモデル、認知パターン
    communication_prefs:     # 言語、トーン、フォーマット

  mutable:                   # 短期可変（現在のコンテキスト）
    current_roles: []
    current_projects: []
    constraints_now: {}

  learning_log:              # 学習記録
    corrections_that_worked: []
    common_pitfalls: []

  agent_runtime_policy:      # Agent の振る舞い設定
    hypotheses: []           # Agent の仮説（検証待ち）
    behavioral_observations: []  # 行動観察ログ

  deep_self_structure:       # 7層の深層自己構造
    layer1_manifest_identity:    # 顕在アイデンティティ
    layer2_shadow:               # シャドウ（否認された自己）
    layer3_behavioral_patterns:  # 行動パターン
    layer4_emotional_triggers:   # 感情トリガー
    layer5_core_beliefs:         # コア・ビリーフ
    layer6_internal_contradictions:  # 内的矛盾
    layer7_life_script:          # ライフスクリプト
    synthesis:                   # 強み・盲点・成長点
```

## Skills

| Skill | Description | Trigger |
|-------|-------------|---------|
| `user-model-core` | 初期化、表示、検証 | 「user-model を初期化」「プロファイル表示」 |
| `user-model-evolve` | 会話から学習し更新提案 | 「進化して」「学習して」 |
| `user-model-deep-analysis` | 7層の深層自己構造分析 | 「深層分析して」「自分を分析して」 |
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

## Deep Self Analysis

7層の深層自己構造分析で、本人すら自覚しにくいレイヤーを可視化：

| Layer | 名前 | 内容 |
|-------|------|------|
| 1 | 顕在アイデンティティ | 自覚している性格・価値観・自己像 |
| 2 | シャドウ | 否認された自己、防衛機制 |
| 3 | 行動パターン | 反復構造、stuck loop |
| 4 | 感情トリガー | 強く反応する条件、感情ハイジャック |
| 5 | コア・ビリーフ | 根源的信念、世界観、自己規範 |
| 6 | 内的矛盾 | 言行不一致、自己欺瞞 |
| 7 | ライフスクリプト | 無意識の人生パターン |

```
🔬 深層自己構造分析

【Layer 5: コア・ビリーフ】 confidence: 0.75

世界観:
- 「世界は、構造を見抜いた者にしか動かせない」

自己規範:
- 「理解されないまま動くことは、暴力に近い」

---

【総括】

最大の強み: 思考の初速を、構造として置けること
最大の盲点: "理解されない前提"を、すでに受け入れてしまっていること
成長ポイント: 構造を置く人から、構造が継承される場を設計する人への移行
```

## File Structure

```
user-model-framework/
├── .claude-plugin/
│   └── plugin.json          # Plugin manifest
├── skills/
│   ├── user-model-core/     # 管理統合スキル
│   ├── user-model-evolve/   # 自己進化（仮説検証ループ）
│   ├── user-model-deep-analysis/  # 7層深層分析
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
