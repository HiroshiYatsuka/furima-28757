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
| user_birthday        | string | null: false |

### Association
- has_many :items
- has_many :comments
- belongs_to :card_information

## itemsテーブル
| Column               | Type    | Options     |
|----------------------|---------|-------------|
| exhibitor_id         | string  | null: false |
| item_id              | string  | null: false |
| item_name            | string  | null: false |
| item_category        | string  | null: false |
| item_price           | integer | null: false |
| item_image           | string  | null: false |
| item_status          | string  | null: false |
| item_delivery_fee    | integer | null: false |
| item_shipping_origin | string  | null: false |
| item_shipment        | string  | null: false |

### Association
- belongs_to :user
- has_many :comments

## commentsテーブル
| Column   | Type   | Options                        |
|----------|--------|--------------------------------|
| user_id  | string | null: false, foreign_key: true |
| item_id  | string | null: false, foreign_key: true |
| comment  | string |                                |

### Association
- belongs_to :user
- belongs_to :item

## card_informationテーブル
| Column  | Type   | Options                        |
|---------|--------|--------------------------------|
| user_id | string | null: false, foreign_key: true |
| card_id | string | null: false, foreign_key: true |

### Association
- belongs_to :user