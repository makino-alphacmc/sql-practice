# order_items テーブル サンプルデータ（全12件）

`csv/order_items.csv` / `ec_practice.order_items` の実データ一覧。

## 主要カラム一覧（小計込み）

| order_item_id | order_id | product_id | quantity | unit_price | subtotal (quantity×unit_price) |
| -------------: | -------: | ---------: | -------: | ---------: | -------------------------------: |
| 5001           | 1001     | 101        | 1        | 2800       | 2800                              |
| 5002           | 1001     | 103        | 2        | 1200       | 2400                              |
| 5003           | 1002     | 102        | 1        | 12800      | 12800                             |
| 5004           | 1002     | 103        | 3        | 1200       | 3600                              |
| 5005           | 1003     | 104        | 1        | 32800      | 32800（※注文はcanceled）         |
| 5006           | 1004     | 106        | 4        | 1500       | 6000                              |
| 5007           | 1005     | 105        | 1        | 19800      | 19800                             |
| 5008           | 1006     | 101        | 2        | 2800       | 5600                              |
| 5009           | 1006     | 102        | 1        | 12800      | 12800                             |
| 5010           | 1007     | 104        | 1        | 32800      | 32800                             |
| 5011           | 1008     | 103        | 5        | 1200       | 6000                              |
| 5012           | 1008     | 106        | 2        | 1500       | 3000                              |

## item_options（JSONB）

### order_item_id = 5001
```json
{"color": "black", "gift_wrap": false}
```

### order_item_id = 5002
```json
{"length_m": 1.5, "gift_wrap": false}
```

### order_item_id = 5003
```json
{"switch": "brown", "gift_wrap": true}
```

### order_item_id = 5004
```json
{"length_m": 1.5, "gift_wrap": true}
```

### order_item_id = 5005
```json
{"color": "black", "gift_wrap": false}
```

### order_item_id = 5006
```json
{"grind": "beans", "gift_wrap": false}
```

### order_item_id = 5007
```json
{"color": "gray", "gift_wrap": true}
```

### order_item_id = 5008
```json
{"color": "black", "gift_wrap": false}
```

### order_item_id = 5009
```json
{"switch": "brown", "gift_wrap": false}
```

### order_item_id = 5010
```json
{"color": "black", "gift_wrap": false}
```

### order_item_id = 5011
```json
{"length_m": 1.5, "gift_wrap": true}
```

### order_item_id = 5012
```json
{"grind": "beans", "gift_wrap": true}
```

## 一目で使える集計メモ

- ギフト包装あり（gift_wrap = true）: 5003, 5004, 5007, 5011, 5012
- 注文ごとの合計金額（キャンセル含む）:
  - 1001: 2800+2400 = 5200
  - 1002: 12800+3600 = 16400
  - 1003: 32800（canceledなので売上集計からは通常除外）
  - 1004: 6000
  - 1005: 19800
  - 1006: 5600+12800 = 18400
  - 1007: 32800
  - 1008: 6000+3000 = 9000
- 商品別の販売数量合計: 101→3, 102→2, 103→10, 104→2, 105→1, 106→6
