# products テーブル サンプルデータ（全7件）

`csv/products.csv` / `ec_practice.products` の実データ一覧。

## 主要カラム一覧

| product_id | sku          | product_name         | category     | price | is_active |
| ---------: | ------------ | --------------------- | ------------ | ----: | --------- |
| 101        | MOUSE-001    | ワイヤレスマウス      | PC周辺機器   |  2800 | true      |
| 102        | KEYBOARD-001 | メカニカルキーボード  | PC周辺機器   | 12800 | true      |
| 103        | CABLE-001    | USB-Cケーブル         | アクセサリ   |  1200 | true      |
| 104        | MONITOR-001  | 27インチモニター      | PC周辺機器   | 32800 | true      |
| 105        | CHAIR-001    | オフィスチェア        | 家具         | 19800 | true      |
| 106        | COFFEE-001   | コーヒー豆            | 食品         |  1500 | true      |
| 107        | WEBCAM-OLD   | 旧型Webカメラ         | PC周辺機器   |  4500 | **false** |

## tags（配列）

| product_id | tags                                  |
| ---------: | -------------------------------------- |
| 101        | `{"wireless","gadget","beginner"}`     |
| 102        | `{"keyboard","mechanical","gadget"}`   |
| 103        | `{"usb-c","mobile","gadget"}`          |
| 104        | `{"monitor","display","work"}`         |
| 105        | `{"chair","office","work"}`            |
| 106        | `{"coffee","food"}`                    |
| 107        | `{"webcam","old","gadget"}`            |

## specs（JSONB）

### product_id = 101（ワイヤレスマウス）
```json
{"color": "black", "connection": "bluetooth", "warranty_months": 12, "weight_g": 85}
```

### product_id = 102（メカニカルキーボード）
```json
{"switch": "brown", "layout": "JIS", "backlight": true, "warranty_months": 24}
```

### product_id = 103（USB-Cケーブル）
```json
{"length_m": 1.5, "power_delivery": true, "warranty_months": 6}
```

### product_id = 104（27インチモニター）
```json
{"size_inch": 27, "resolution": "2560x1440", "refresh_rate": 144, "warranty_months": 36}
```

### product_id = 105（オフィスチェア）
```json
{"material": "mesh", "has_headrest": true, "max_weight_kg": 120, "warranty_months": 12}
```

### product_id = 106（コーヒー豆）
```json
{"origin": "Brazil", "roast": "medium", "weight_g": 200}
```

### product_id = 107（旧型Webカメラ）
```json
{"resolution": "720p", "warranty_months": 0, "reason_inactive": "discontinued"}
```

## 一目で使える集計メモ

- 非アクティブ商品: product_id 107 のみ
- カテゴリ: PC周辺機器(101,102,104,107) / アクセサリ(103) / 家具(105) / 食品(106)
- gadgetタグあり: 101, 102, 103, 107
- warranty_months >= 12: 101(12), 102(24), 104(36), 105(12)
- 価格10,000円以上: 102(12800), 104(32800), 105(19800)
