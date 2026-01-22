---
name: user-model-update-mutable
description: user_model.yaml の mutable セクションを更新する。「今のプロジェクトは」「役割が変わった」「今週のフォーカスは」などで発火。
---

# Update Mutable Skill

User Model の `mutable` セクション（短期可変情報）を更新します。

> **設定**: パスは `user-model-core/config.yaml` を参照

## 対象フィールド

| フィールド | 内容 |
|-----------|------|
| `current_roles` | 現在の役割 |
| `current_projects` | 進行中のプロジェクト |
| `current_focus_topics` | 今フォーカスしているトピック |
| `constraints_now` | 現在の制約（時間、予算、エネルギー） |
| `review_at` | 次回見直し日 |

## 更新手順

1. **対象特定**: ユーザーの指示から更新対象を特定
2. **変更案作成**: 新しい値を構造化
3. **確認**: 簡潔に提示して承認を得る
4. **更新実行**: yaml ファイルを更新
5. **review_at 更新**: 30日後に設定

## プロジェクト追加の例

```yaml
current_projects:
  - name: "AI Agent 環境構築"
    objective: "自分を理解する Agent を作る"
    constraints:
      - "chezmoi で管理"
      - "Claude Code + Cursor で共有"
    current_state: "user_model.yaml 設計中"
    next_actions:
      - "Skills 実装"
      - "自己進化機能の実装"
    review_at: "2026-02-01"
```

## 出力フォーマット

```
📝 mutable 更新

+ current_projects に追加:
  - name: "AI Agent 環境構築"
    objective: "自分を理解する Agent を作る"
    ...

[Y] 更新 / [N] キャンセル
```

## 注意

- mutable は頻繁に変わる情報。気軽に更新 OK
- 古いプロジェクトは削除 or アーカイブを提案
