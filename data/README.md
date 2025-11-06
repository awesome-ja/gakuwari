# 📊 Gakuwari データベース

このディレクトリには、学割サービス情報の構造化データが含まれています。

## ファイル一覧

- **`services.json`** - 全学割サービスの機械読み取り可能なデータベース
- **`schema.json`** - データ構造のJSON Schema定義
- **`README.md`** - このファイル（使い方ガイド）

## データ形式

データはJSON形式で、以下の構造を持っています：

```json
{
  "version": "1.0.0",
  "lastUpdated": "2025-11-05",
  "categories": [
    {
      "id": "development",
      "name": "開発・プログラミング",
      "nameEn": "Development & Programming",
      "icon": "🔧",
      "services": [...]
    }
  ],
  "metadata": {...}
}
```

### サービスオブジェクト

各サービスは以下の情報を含みます：

```json
{
  "id": "github-pro",
  "name": "GitHub Pro",
  "provider": "GitHub",
  "type": "subscription",
  "discount": {
    "type": "free",
    "duration": "2年間",
    "originalPrice": null,
    "studentPrice": 0,
    "currency": "JPY"
  },
  "eligibility": {
    "studentTypes": ["大学生", "大学院生"],
    "requirements": ["学生証明"]
  },
  "verificationMethod": "GitHub Student Developer Pack",
  "url": "https://education.github.com/pack",
  "status": "active",
  "lastVerified": null,
  "notes": "GitHub Student Developer Packで2年間無料"
}
```

## 使用方法

### JavaScriptでの読み込み

```javascript
// Node.js
const services = require('./data/services.json');

// カテゴリ一覧を取得
console.log(services.categories.map(c => c.name));

// 開発カテゴリのサービスを取得
const devServices = services.categories.find(c => c.id === 'development').services;

// 無料サービスのみをフィルタ
const freeServices = services.categories
  .flatMap(c => c.services)
  .filter(s => s.discount.type === 'free');
```

### Pythonでの読み込み

```python
import json

# データを読み込む
with open('data/services.json', 'r', encoding='utf-8') as f:
    data = json.load(f)

# カテゴリ一覧を表示
for category in data['categories']:
    print(f"{category['icon']} {category['name']}")
    print(f"  サービス数: {len(category['services'])}")

# 大学生向けサービスを検索
for category in data['categories']:
    for service in category['services']:
        if '大学生' in service['eligibility']['studentTypes']:
            print(f"- {service['name']} ({service['provider']})")
```

### curlでの取得

```bash
# GitHubから最新版を取得
curl -o services.json https://raw.githubusercontent.com/awesome-ja/gakuwari/main/data/services.json
```

## データ検証

JSON Schemaを使用してデータの妥当性を検証できます：

```bash
# ajv-cliを使用した検証
npm install -g ajv-cli
ajv validate -s data/schema.json -d data/services.json
```

## フィールド説明

### サービスタイプ (`type`)
- `subscription` - サブスクリプションサービス
- `license` - ライセンス提供
- `credit` - クレジット/ポイント付与
- `discount` - 一般的な割引

### 割引タイプ (`discount.type`)
- `free` - 完全無料
- `percentage` - パーセンテージ割引
- `fixed-amount` - 固定金額割引
- `credit` - クレジット付与
- `student-plan` - 学生専用プラン
- `student-discount` - 学生割引
- `institutional` - 教育機関経由の提供

### ステータス (`status`)
- `active` - 現在利用可能
- `inactive` - 一時的に利用不可
- `discontinued` - 終了済み
- `unknown` - 状態不明

## API使用例

このデータを使用したアプリケーション例：

### 1. カテゴリ別サービス数の集計

```javascript
const categoryCounts = services.categories.map(cat => ({
  name: cat.name,
  count: cat.services.length,
  freeCount: cat.services.filter(s => s.discount.type === 'free').length
}));
```

### 2. プロバイダー別サービス一覧

```javascript
const byProvider = {};
services.categories.forEach(cat => {
  cat.services.forEach(service => {
    if (!byProvider[service.provider]) {
      byProvider[service.provider] = [];
    }
    byProvider[service.provider].push(service);
  });
});
```

### 3. 学生タイプでフィルタリング

```javascript
function findServicesForStudent(studentType) {
  const results = [];
  services.categories.forEach(cat => {
    cat.services.forEach(service => {
      if (service.eligibility.studentTypes.includes(studentType)) {
        results.push({
          category: cat.name,
          service: service.name,
          provider: service.provider,
          url: service.url
        });
      }
    });
  });
  return results;
}

// 高校生向けサービスを検索
const highSchoolServices = findServicesForStudent('高校生');
```

## データ更新

データに変更がある場合は、以下を行ってください：

1. `services.json` を更新
2. `lastUpdated` フィールドを現在の日付に更新
3. 変更があったサービスの `lastVerified` を更新
4. `metadata.totalServices` を更新（サービス数が変わった場合）

## ライセンス

このデータはMITライセンスの下で提供されています。

## コントリビューション

データの更新や修正は、プルリクエストまたはIssueでお知らせください。

- 新しいサービスを追加
- 価格情報を更新
- リンク切れを修正
- 終了したサービスのステータスを更新

詳細は [CONTRIBUTING.md](../CONTRIBUTING.md) をご覧ください。
