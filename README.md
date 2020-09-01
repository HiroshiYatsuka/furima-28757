# README

## usersテーブル
| Column               | Type   | Options     |
| ---------------------|--------|-------------|
| nickname             | string | null: false |
| email                | string | null: false |
| password             | string | null: false |
| family_name          | string | null: false |
| first_name           | string | null: false |
| family_name_furigana | string | null: false |
| first_name_furigana  | string | null: false |
| birthday             | date   | null: false |

### Association
- has_many :items
- has_many :comments
- has_many :item_buyer

## itemsテーブル
| Colum              | Type       | Options                        |
|--------------------|------------|--------------------------------|
| user               | references | null: false, foreign_key: true |
| name               | string     | null: false                    |
| price              | integer    | null: false                    |
| category_id        | integer    | null: false                    |
| status_id          | integer    | null: false                    |
| description        | text       | null: false                    |
| delivery_fee_id    | integer    | null: false                    |
| shipping_origin_id | integer    | null: false                    |
| shipment_id        | integer    | null: false                    |

### Association
- belongs_to :user
- has_many :comments
- has_one :item_buyer
- belongs_to_active_hash :category_id
- belongs_to_active_hash :status_id
- belongs_to_active_hash :delivery_fee_id
- belongs_to_active_hash :shipping_origin_id
- belongs_to_active_hash :shipment_id

## commentsテーブル
| Column   | Type   | Options                        |
|----------|--------|--------------------------------|
| user_id  | string | null: false, foreign_key: true |
| item_id  | string | null: false, foreign_key: true |
| comment  | string |                                |

### Association
- belongs_to :user
- belongs_to :item

## item_buyersテーブル
| Column  | Typ     | Options                        |
| --------|---------|--------------------------------|
| user_id | integer | null: false, foreign_key: true |
| item_id | integer | null: false, foreign_key: true |

### Association
- belongs_to :user
- belongs_to :item
- has_one :address

## Addressesテーブル
| Column        | Type       | Options                        |
| --------------|------------|--------------------------------|
| post_code     | string     |                                |
| prefecture    | integer    |                                |
| city          | string     | null: false                    |
| address       | string     |                                |
| building_name | string     |                                |
| phone_number  | string     | null: false                    |
| buyer         | references | null: false, foreign_key: true |

### Association
- belongs_to :item_buyer
- belongs_to_active_hash :prefecture