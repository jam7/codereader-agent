# コード読解エージェント

汎用的なコード読解エージェントシステム。プロジェクトのコードを体系的に分析し、構造化ドキュメントと関数詳細ドキュメントを自動生成。

## エージェント一覧

| エージェント | 絵文字 | 役割 | 成果物 |
|------------|-------|------|--------|
| **codereader.planner** | 📋 | 読解計画立案 | `analysis/<project>/plan.md` |
| **codereader.investigator** | 🔍 | コード調査・分析 | `analysis/<project>/investigation/` |
| **codereader.structure-documenter** | 🗺️ | 構造ドキュメント生成 | `analysis/<project>/{overview,architecture,data-flow,modules}.md` |
| **codereader.function-documenter** | 📚 | 関数詳細ドキュメント生成 | `analysis/<project>/functions/*.md` |
| **codereader.reviewer** | ✅ | ドキュメント検証 | `analysis/<project>/review-result.md` |

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

## 使い方

1. **読解開始**: `@codereader.planner` を呼び出し、読解対象を指定
2. **自動実行**: エージェント間で自動ハンドオフされ、ドキュメント生成まで完了
3. **結果確認**: `analysis/<project-name>/` にドキュメントが生成される

## 生成されるドキュメント

### 構造化ドキュメント
- **overview.md**: プロジェクト概要、技術スタック、エントリーポイント
- **architecture.md**: アーキテクチャ図、コンポーネント説明、依存関係
- **data-flow.md**: データフローシーケンス図、データ変換、エラーハンドリング
- **modules/*.md**: 各モジュールの詳細説明

### 関数詳細ドキュメント
- **functions/*.md**: 全関数の網羅的説明
  - 入力/出力
  - 処理内容（ステップバイステップ）
  - データ構造・変数の使い方
  - アルゴリズム工夫点（高速化、メモリ効率化）
  - 全体の流れ（結論）

## ディレクトリ構造

```
analysis/
  <project-name>/
    plan.md                       # 調査計画書
    overview.md                   # プロジェクト概要
    architecture.md               # アーキテクチャ
    data-flow.md                  # データフロー
    review-result.md              # レビュー結果
    investigation/                # 調査結果（中間生成物）
      structure.md
      components.md
      dataflow.md
      algorithms.md
      functions-list.md
    modules/                      # モジュール別ドキュメント
      <module-name>.md
    functions/                    # 関数詳細ドキュメント
      <module-name>-functions.md
```

## 特徴

- **言語非依存**: あらゆるプログラミング言語に対応
- **サブエージェント活用**: 複雑な調査でコンテキスト汚染を回避
- **反復改善**: レビューエージェントが品質をチェックし、不足があれば追加調査
- **網羅的**: 構造と関数の両面から完全に文書化

## 参考ドキュメント

- `docs/code-reading-guidelines.md`: コード読解のベストプラクティス、分析観点、ドキュメント品質基準
