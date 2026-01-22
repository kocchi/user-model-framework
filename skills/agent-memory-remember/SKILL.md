---
name: agent-memory-remember
description: 作業内容や重要な情報を記憶する。「記憶して」「覚えて」「メモして」「保存して」などで発火。
---

# Remember Skill

ユーザーが「記憶して」「覚えて」「メモして」「保存して」と言った時に、指定された情報を永続化します。

## 記憶の保存場所

プロジェクトルートに `.memories/` ディレクトリを作成し、Markdown ファイルとして保存します。

```
.memories/
├── 2026-01-22_api-design.md
├── 2026-01-22_auth-flow.md
└── index.md
```

## 保存手順

1. **ディレクトリ確認**: `.memories/` が存在しない場合は作成
2. **ファイル名生成**: `YYYY-MM-DD_<slug>.md` 形式
3. **内容構造化**:

```markdown
# <タイトル>

Created: YYYY-MM-DD HH:MM
Tags: #tag1 #tag2

## Summary
<1-2行の要約>

## Details
<詳細な内容>

## Related
- <関連ファイルへのリンク>
```

4. **index.md 更新**: 新しいエントリを追加

## index.md の形式

```markdown
# Memory Index

## Recent
- [2026-01-22] [API設計方針](./2026-01-22_api-design.md) - RESTful API の設計ルール
- [2026-01-22] [認証フロー](./2026-01-22_auth-flow.md) - OAuth2 + JWT の実装方針

## By Tag
### #api
- [API設計方針](./2026-01-22_api-design.md)

### #auth
- [認証フロー](./2026-01-22_auth-flow.md)
```

## 重要

- 既存の記憶と重複する場合は、既存ファイルを更新
- タグは内容から自動推測
- 要約は検索しやすいように具体的に記述

## 応答例

「✅ 記憶しました: `.memories/2026-01-22_api-design.md`」
