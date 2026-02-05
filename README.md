# コード読解エージェント

汎用的なコード読解エージェントシステム。プロジェクトのコードを体系的に分析し、構造化ドキュメントと関数詳細ドキュメントを自動生成。

## 使い方

1. **読解開始**: `@codereader.planner` を呼び出し、読解対象を指定
2. **自動実行**: エージェント間で自動ハンドオフされ、ドキュメント生成まで完了
3. **結果確認**: `analysis/<project-name>/` にドキュメントが生成される

## エージェント一覧

| エージェント | 絵文字 | 役割 | 詳細 |
|------------|-------|------|------|
| **codereader.planner** | 📋 | 読解計画立案 | [詳細](agents/codereader.planner.agent.md) |
| **codereader.investigator** | 🔍 | コード調査・分析 | [詳細](agents/codereader.investigator.agent.md) |
| **codereader.structure-documenter** | 🗺️ | 構造ドキュメント生成 | [詳細](agents/codereader.structure-documenter.agent.md) |
| **codereader.function-documenter** | 📚 | 関数詳細ドキュメント生成 | [詳細](agents/codereader.function-documenter.agent.md) |
| **codereader.reviewer** | ✅ | ドキュメント検証 | [詳細](agents/codereader.reviewer.agent.md) |

各エージェントファイルには、ワークフロー全体での位置、生成する成果物、実行手順の詳細が記載されています。

## ワークフロー

```
📋 計画立案
    ↓
🔍 コード調査（サブエージェント活用）
    ↓
🗺️ 構造ドキュメント生成
    ↓
📚 関数詳細ドキュメント生成
    ↓
✅ レビュー・検証
    ↓ (不足あり)
    └→ 🔍 追加調査 or 🗺️📚 修正
```

## 特徴

- **言語非依存**: あらゆるプログラミング言語に対応
- **サブエージェント活用**: 複雑な調査でコンテキスト汚染を回避
- **反復改善**: レビューエージェントが品質をチェックし、不足があれば追加調査
- **網羅的**: 構造と関数の両面から完全に文書化

## 参考ドキュメント

- [code-reading-guidelines.md](docs/code-reading-guidelines.md): コード読解のベストプラクティス、分析観点、ドキュメント品質基準
