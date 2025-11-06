# サービス追加テンプレート

新しい学割サービスを追加する際は、このテンプレートを参考にしてください。

## README.md への追加

```markdown
### サービス名
- **プラン名**: 説明
- **通常価格**: ¥X,XXX/月（または年額）
- **学割価格**: ¥XXX/月（または割引率）
- **対象**: 対象となる学生（例: 大学生、高校生、専門学校生など）
- **必要書類**: 学生証、学校メールアドレスなど
- **特徴**: 主な機能や特典
- **URL**: https://example.com/student
- **最終確認日**: YYYY-MM-DD
```

## data/services.json への追加

新しいサービスを追加する場合、対応するカテゴリの `services` 配列に以下の形式で追加してください：

```json
{
  "id": "service-name",
  "name": "サービス名",
  "provider": "提供企業名",
  "type": "subscription",
  "discount": {
    "type": "percentage",
    "percentOff": 50,
    "duration": "学生期間中",
    "originalPrice": 1000,
    "studentPrice": 500,
    "currency": "JPY"
  },
  "eligibility": {
    "studentTypes": ["大学生", "大学院生"],
    "requirements": ["学生証明書"]
  },
  "verificationMethod": "学生証明書",
  "url": "https://example.com/student",
  "status": "active",
  "lastVerified": "2025-11-05",
  "notes": "補足情報"
}
```

## フィールドの説明

### 必須フィールド

- **id**: 一意の識別子（小文字、ハイフン区切り）
- **name**: サービス名（日本語）
- **provider**: 提供企業名
- **type**: サービスタイプ
  - `subscription` - サブスクリプション
  - `license` - ライセンス
  - `credit` - クレジット/ポイント
  - `discount` - 一般的な割引
- **url**: 公式サービスURL
- **status**: サービス状態
  - `active` - 現在利用可能
  - `inactive` - 一時的に利用不可
  - `discontinued` - 終了済み
  - `unknown` - 状態不明

### discount オブジェクト

- **type**: 割引タイプ
  - `free` - 完全無料
  - `percentage` - パーセンテージ割引
  - `fixed-amount` - 固定金額割引
  - `credit` - クレジット付与
  - `student-plan` - 学生専用プラン
  - `institutional` - 教育機関経由
- **percentOff**: 割引率（percentage の場合）
- **duration**: 割引期間の説明
- **originalPrice**: 通常価格（数値、わからない場合は `null`）
- **studentPrice**: 学割価格（数値、わからない場合は `null`）
- **currency**: 通貨コード（例: `"JPY"`, `"USD"`）

### eligibility オブジェクト

- **studentTypes**: 対象学生タイプの配列
  - 例: `["大学生", "大学院生", "高校生", "専門学校生"]`
- **requirements**: 必要な条件の配列
  - 例: `["学生証明書", "学校メールアドレス"]`
- **exclusions**: 除外条件（オプション）

### その他のフィールド

- **verificationMethod**: 学生認証方法
- **lastVerified**: 最終確認日（YYYY-MM-DD形式、わからない場合は `null`）
- **features**: 含まれる機能の配列（オプション）
- **notes**: 補足情報（日本語）

## チェックリスト

新しいサービスを追加する前に、以下を確認してください：

- [ ] 公式サイトで学割情報を確認した
- [ ] 対象となる学生の種類を確認した
- [ ] 価格情報が正確である
- [ ] URLが正しく、アクセス可能である
- [ ] 既存のサービスと重複していない
- [ ] `id` が一意である
- [ ] JSON構文が正しい（`jq` や JSON validator で検証）
- [ ] README.md と services.json の両方を更新した
- [ ] 適切なカテゴリに追加した

## 情報源

情報を追加する際は、以下のような信頼できる情報源から取得してください：

- ✅ 公式サイト
- ✅ 公式ブログ・プレスリリース
- ✅ 公式SNSアカウント
- ❌ 個人ブログ（確認が必要）
- ❌ 古い情報（要確認）

## 例

### 良い例

```json
{
  "id": "spotify-premium-student",
  "name": "Spotify Premium Student",
  "provider": "Spotify",
  "type": "subscription",
  "discount": {
    "type": "percentage",
    "percentOff": 50,
    "duration": "学生期間中",
    "originalPrice": 980,
    "studentPrice": 490,
    "currency": "JPY"
  },
  "eligibility": {
    "studentTypes": ["大学生", "短大生", "大学院生", "専門学校生", "高専生"],
    "requirements": ["学生証明書"],
    "exclusions": ["高校生以下は対象外"]
  },
  "verificationMethod": "SheerID",
  "url": "https://www.spotify.com/jp/student/",
  "status": "active",
  "lastVerified": "2025-11-05",
  "notes": "通常の半額程度、高校生以下は対象外"
}
```

## ヘルプ

質問や不明点がある場合は：

- [Issue](../../issues) を開いて質問
- [Discussion](../../discussions) で相談
- [CONTRIBUTING.md](../CONTRIBUTING.md) を参照

皆様のコントリビューションをお待ちしています！
