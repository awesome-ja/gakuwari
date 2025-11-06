# Changelog

このファイルはプロジェクトのすべての重要な変更を記録します。

フォーマットは [Keep a Changelog](https://keepachangelog.com/ja/1.0.0/) に基づいており、
このプロジェクトは [Semantic Versioning](https://semver.org/lang/ja/) に準拠しています。

## [Unreleased]

### Added
- 📊 構造化データフォーマット（JSON）を追加
  - `data/services.json` - 全学割サービスの機械読み取り可能なデータベース
  - `data/schema.json` - JSON Schemaによるデータ検証
  - `data/README.md` - データの使用方法ガイド
- 🌐 英語翻訳を追加（`README.en.md`）
- 📊 サービス比較表を追加（`COMPARISON.md`）
  - 音楽ストリーミングサービス比較
  - 動画配信サービス比較
  - 開発ツール比較
  - クリエイティブツール比較
  - クラウドストレージ比較
  - オンライン学習プラットフォーム比較
  - ハードウェア購入比較
- 🎮 新カテゴリ「ゲーム・エスポーツ」を追加
  - Discord Nitro学生割引
  - Unity Pro / Unity Student
  - Unreal Engine
  - Nintendo Switch Online
  - PlayStation Plus
- 📖 新カテゴリ「オンライン学習」を追加
  - Udemy
  - Coursera
  - edX
  - Skillshare
  - LinkedIn Learning
  - Pluralsight
- ☁️ 新カテゴリ「クラウド・ストレージ」を追加
  - Google Workspace for Education
  - Microsoft OneDrive
  - Dropbox Education
  - Box for Education
  - AWS Educate
  - GCP Education Grants
- 🚆 新カテゴリ「交通・移動」を追加
  - JR通学定期
  - 私鉄・地下鉄通学定期
  - 航空券学生割引
  - 高速バス学生割引
- 🛒 新カテゴリ「ハードウェア・ショッピング」を追加
  - Apple Education Store
  - Microsoft Store Education
  - Dell University
  - HP Education Store
  - Lenovo 学生ストア
- 📺 動画配信サービスを追加
  - Netflix（学割情報）
  - Hulu（学割情報）
  - U-NEXT（学割情報）
- 🤖 自動化ワークフローを追加
  - `.github/workflows/link-check.yml` - 自動リンクチェック
  - `.github/workflows/validate-data.yml` - JSONデータ検証

### Changed
- 🔧 GitHubテンプレートを更新
  - Issue テンプレート（bug_report.yml）を学割プロジェクト向けに最適化
  - Pull Request テンプレートを文書プロジェクト向けに更新
  - config.yml のリンクを gakuwari プロジェクトに更新
- 📖 目次に新カテゴリを追加

### Fixed
- 🔗 古いURL-Note-Takerプロジェクトへの参照を削除
- 🐛 Bug reportテンプレートから不要なブラウザ/ユーザースクリプトフィールドを削除
- 📝 Pull Requestテンプレートから不適切なテスト項目を削除

## [1.0.0] - 2025-11-05

### Added
- 🎉 初回リリース
- 🔧 開発・プログラミングカテゴリ
  - GitHub Pro / GitHub Copilot
  - JetBrains製品（IntelliJ IDEA, PyCharm, WebStorm, CLion）
  - Microsoft製品（Visual Studio, Azure, Office 365）
- 🎨 クリエイティブ・デザインカテゴリ
  - Adobe Creative Cloud
  - Autodesk製品（AutoCAD, Maya, Fusion 360, 3ds Max）
  - Maxon Cinema 4D
- 🎵 音楽・エンターテイメントカテゴリ
  - Spotify Premium Student
  - YouTube Music
  - Apple Music
  - Amazon Music
  - AWA
  - 楽天ミュージック
  - TOWER RECORDS MUSIC
- 📺 動画配信カテゴリ
  - Amazon Prime Video (Prime Student)
- 🛍️ ライフスタイル・サービスカテゴリ
  - Amazon Prime Student
- 📚 学習・教育カテゴリ
  - ChatGPT Plus
  - Notion for Education
  - Claude Pro
- 📖 参考記事・リソースカテゴリ
- 📝 CONTRIBUTING.md - コントリビューションガイドライン
- 🐛 GitHubテンプレート
  - Issue templates（bug_report, feature_request）
  - Discussion templates（general, help, ideas, show-and-tell）
  - Pull request template
- ⚖️ MIT License

## 変更タイプの定義

- `Added` - 新機能・新サービス
- `Changed` - 既存機能の変更
- `Deprecated` - 非推奨になった機能
- `Removed` - 削除された機能・サービス
- `Fixed` - バグ修正
- `Security` - セキュリティ関連の修正

## コントリビューター向け情報

### CHANGELOGの更新方法

1. **新しいサービスを追加した場合**
   ```markdown
   ### Added
   - サービス名とカテゴリを記載
   ```

2. **既存サービス情報を更新した場合**
   ```markdown
   ### Changed
   - サービス名と変更内容を記載
   ```

3. **サービスが終了した場合**
   ```markdown
   ### Removed
   - サービス名と終了理由を記載
   ```

4. **価格が変更された場合**
   ```markdown
   ### Changed
   - サービス名: 旧価格 → 新価格
   ```

### バージョニング

このプロジェクトは Semantic Versioning を使用しています：

- **MAJOR (X.0.0)**: 大幅な構造変更や破壊的変更
- **MINOR (0.X.0)**: 新カテゴリ追加、機能追加
- **PATCH (0.0.X)**: バグ修正、情報更新、サービス追加

---

詳細は [README.md](README.md) をご覧ください。
