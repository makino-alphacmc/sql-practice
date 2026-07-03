# customers テーブル サンプルデータ（全6件）

`csv/customers.csv` / `ec_practice.customers` の実データ一覧。問題を解くときにこのファイルを見れば、期待結果を自分で検算できます。

## 主要カラム一覧

| customer_id | customer_name    | email                       | prefecture | registered_at |
| ----------: | ---------------- | ---------------------------- | ---------- | -------------- |
| 1           | 佐藤 花子        | hanako.sato@example.com      | 東京都     | 2025-01-05     |
| 2           | 鈴木 太郎        | taro.suzuki@example.com      | 埼玉県     | 2025-01-20     |
| 3           | 田中 美香        | mika.tanaka@example.com      | 大阪府     | 2025-02-10     |
| 4           | 牧野 ジェリエル  | jaleel.makino@example.com    | 埼玉県     | 2025-02-15     |
| 5           | 山田 健          | ken.yamada@example.com       | 神奈川県   | 2025-03-01     |
| 6           | 小林 葵          | aoi.kobayashi@example.com    | 東京都     | 2025-03-12     |

## phone_numbers（配列）

| customer_id | phone_numbers                     |
| ----------: | ---------------------------------- |
| 1           | `{"090-1111-1111","03-1111-1111"}` |
| 2           | `{"080-2222-2222"}`                |
| 3           | `{"070-3333-3333"}`                |
| 4           | `{"090-4444-4444","0493-44-4444"}` |
| 5           | `{"080-5555-5555"}`                |
| 6           | `{"070-6666-6666"}`                |

## profile（JSONB）

### customer_id = 1
```json
{"rank": "gold", "age_group": "30s", "interests": ["travel", "coffee", "gadget"], "notification": {"email": true, "sms": false}}
```

### customer_id = 2
```json
{"rank": "silver", "age_group": "40s", "interests": ["desk_setup", "keyboard"], "notification": {"email": true, "sms": true}}
```

### customer_id = 3
```json
{"rank": "bronze", "age_group": "20s", "interests": ["food", "coffee"], "notification": {"email": false, "sms": true}}
```

### customer_id = 4
```json
{"rank": "gold", "age_group": "30s", "interests": ["travel", "drive", "gadget"], "notification": {"email": true, "sms": true}}
```

### customer_id = 5
```json
{"rank": "silver", "age_group": "50s", "interests": ["office", "chair"], "notification": {"email": true, "sms": false}}
```

### customer_id = 6
```json
{"rank": "bronze", "age_group": "20s", "interests": ["gadget", "monitor"], "notification": {"email": false, "sms": false}}
```

## 一目で使える集計メモ

- 都道府県: 東京都(1,6) / 埼玉県(2,4) / 大阪府(3) / 神奈川県(5)
- ランク: gold(1,4) / silver(2,5) / bronze(3,6)
- gadgetに興味あり: customer_id 1, 4, 6
- travelに興味あり: customer_id 1, 4
