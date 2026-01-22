---
name: user-model-update-stable
description: user_model.yaml の stable セクションを更新する。「価値観を追加」「思考スタイルを変更」「コミュニケーション設定を更新」などで発火。
---

# Update Stable Skill

User Model の `stable` セクション（長期安定情報）を更新します。

> **設定**: パスは `user-model-core/config.yaml` を参照

## 対象セクション

| セクション | 内容 |
|-----------|------|
| `north_star` | 長期目標、成功の定義、非妥協点、アンチゴール |
| `decision_engine` | 価値観、品質基準、トレードオフポリシー |
| `thinking_os` | メンタルモデル、問いのスタイル、協働スタイル |
| `communication_prefs` | 言語、トーン、フォーマット、対話契約 |
| `privacy_and_boundaries` | 保存OK/NG、マスクルール |

## 更新手順

1. **対象特定**: ユーザーの指示から更新対象を特定
2. **現在値確認**: User Model を読み込み現在値を提示
3. **変更案提示**: 変更前 → 変更後を diff 形式で提示
4. **確認**: ユーザーの承認を得る
5. **更新実行**: yaml ファイルを更新
6. **メタデータ追加**: `learning_log.calibration_notes` に変更理由を記録

## 出力フォーマット

```
📝 stable セクションの更新提案

対象: stable.decision_engine.values

変更前:
  - name: "検査可能性"
    meaning: "合意できる抽象度で検証できる状態を作る"
    priority: "must"

変更後:
  - name: "検査可能性"
    meaning: "合意できる抽象度で検証できる状態を作る"
    priority: "must"
+ - name: "再現性"
+   meaning: "同じ入力に対して同じ出力が得られる"
+   priority: "should"

[Y] 更新する / [N] キャンセル / [E] 編集
```

## 注意

- stable は長期安定情報。慎重に更新する
- 大きな変更は理由を記録する
- `review_at` を 180 日後に設定
