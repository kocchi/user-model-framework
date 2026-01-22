---
name: user-model-log-learning
description: user_model.yaml の learning_log に学習を記録する。「これは効いた」「この指摘は良かった」「落とし穴を追加」などで発火。
---

# Log Learning Skill

User Model の `learning_log` セクションに学習を記録します。

> **設定**: パスは `user-model-core/config.yaml` を参照

## 対象フィールド

| フィールド | 内容 |
|-----------|------|
| `corrections_that_worked` | 効果があった指摘・介入 |
| `common_pitfalls` | よくある落とし穴 |
| `calibration_notes` | 調整メモ |

## corrections_that_worked のフォーマット

```yaml
- context: "OKR設計"
  issue: "実行プランが尻切れ"
  intervention: "因果仮説→検証観点→会議設計へ落とす"
  outcome: "意思決定が進んだ"
  confidence: 0.7
  date: "2026-01-22"
```

## 記録手順

1. **文脈把握**: 何が効いたのか、なぜ効いたのかを特定
2. **構造化**: 上記フォーマットに変換
3. **確認**: 簡潔に提示
4. **追記**: yaml に追加

## 出力フォーマット

```
📚 learning_log に追記

corrections_that_worked:
+ - context: "選択肢の提示"
+   issue: "毎回入力が長い"
+   intervention: "記号で一発選択できる形式に"
+   outcome: "入力の手間が減った"
+   confidence: 0.8
+   date: "2026-01-22"

[Y] 記録 / [N] キャンセル
```

## 自動検知

以下を検知したら、記録を提案する：

- 「これいいね」「助かった」「効いた」
- ユーザーが明示的に評価した場合
- 同じパターンが複数回成功した場合
