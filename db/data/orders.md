# orders テーブル サンプルデータ（全8件）

`csv/orders.csv` / `ec_practice.orders` の実データ一覧。

## 主要カラム一覧

| order_id | customer_id | order_date          | status        | payment_method |
| -------: | ----------: | -------------------- | ------------- | --------------- |
| 1001     | 1           | 2025-03-01 10:15:00  | shipped       | card            |
| 1002     | 2           | 2025-03-03 14:20:00  | shipped       | bank            |
| 1003     | 1           | 2025-03-10 09:05:00  | **canceled**  | card            |
| 1004     | 3           | 2025-03-12 18:30:00  | shipped       | card            |
| 1005     | 4           | 2025-03-15 21:10:00  | pending       | convenience     |
| 1006     | 5           | 2025-03-20 11:45:00  | shipped       | card            |
| 1007     | 2           | 2025-04-01 08:25:00  | shipped       | card            |
| 1008     | 6           | 2025-04-05 16:40:00  | pending       | bank            |

## coupon_codes（配列）

| order_id | coupon_codes                        |
| -------: | ------------------------------------ |
| 1001     | `{"WELCOME10"}`                      |
| 1002     | `{"SPRINGSALE","KEYBOARD500"}`       |
| 1003     | `{}`（未使用）                       |
| 1004     | `{"FOOD100"}`                        |
| 1005     | `{"WELCOME10"}`                      |
| 1006     | `{}`（未使用）                       |
| 1007     | `{"MONITOR1000"}`                    |
| 1008     | `{"WELCOME10","COFFEE50"}`           |

## delivery_address（JSONB）

| order_id | zip       | prefecture | city       | is_remote_area |
| -------: | --------- | ---------- | ---------- | --------------- |
| 1001     | 100-0001  | 東京都     | 千代田区   | false           |
| 1002     | 330-0001  | 埼玉県     | さいたま市 | false           |
| 1003     | 100-0001  | 東京都     | 千代田区   | false           |
| 1004     | 530-0001  | 大阪府     | 大阪市     | false           |
| 1005     | 355-0001  | 埼玉県     | 東松山市   | false           |
| 1006     | 220-0001  | 神奈川県   | 横浜市     | false           |
| 1007     | 330-0001  | 埼玉県     | さいたま市 | false           |
| 1008     | 160-0001  | 東京都     | 新宿区     | false           |

## order_note（JSONB）

### order_id = 1001
```json
{"gift": false, "source": "web"}
```

### order_id = 1002
```json
{"gift": true, "source": "web"}
```

### order_id = 1003（キャンセル）
```json
{"gift": false, "cancel_reason": "customer_request", "source": "app"}
```

### order_id = 1004
```json
{"gift": false, "source": "app"}
```

### order_id = 1005
```json
{"gift": true, "source": "web", "memo": "新居用"}
```

### order_id = 1006
```json
{"gift": false, "source": "web"}
```

### order_id = 1007
```json
{"gift": false, "source": "web"}
```

### order_id = 1008
```json
{"gift": true, "source": "app"}
```

## 一目で使える集計メモ

- キャンセル注文: order_id 1003（customer_id 1）
- ギフト注文（gift = true）: 1002, 1005, 1008
- WELCOME10クーポン使用: 1001, 1005, 1008
- クーポン未使用（空配列）: 1003, 1006
- 流入元 source: web(1001,1002,1005,1006,1007) / app(1003,1004,1008)
- 支払い方法: card(1001,1003,1004,1006,1007) / bank(1002,1008) / convenience(1005)
