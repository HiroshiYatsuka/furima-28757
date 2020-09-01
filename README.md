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
| birthday        | date   | null: false |

### Association
- has_many :items
- has_many :comments
- has_many :buyer

## itemsテーブル
| Colum           | Type    | Options     |
|-----------------|---------|-------------|
| name            | string  | null: false |
| price           | integer | null: false |
| image           | string  | null: false |
| category        | integer | null: false |
| status          | integer | null: false |
| description     | text    | null: false |
| delivery_fee    | integer | null: false |
| shipping_origin | integer | null: false |
| shipment        | integer | null: false |

### Association
- belongs_to :user
- has_many :comments
- has_one :buyer
- belongs_to_active_hash :category
- belongs_to_active_hash :status
- belongs_to_active_hash :delivery_fee
- belongs_to_active_hash :shipping_origin
- belongs_to_active_hash :shipment

## commentsテーブル
| Column   | Type   | Options                        |
|----------|--------|--------------------------------|
| user_id  | string | null: false, foreign_key: true |
| item_id  | string | null: false, foreign_key: true |
| comment  | string |                                |

### Association
- belongs_to :user
- belongs_to :item

## buyersテーブル
| Column  | Type       | Options                        |
| --------|------------|--------------------------------|
| user_id | references | null: false, foreign_key: true |
| item_id | references | null: false, foreign_key: true |

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
| address       | string     |
| building_name | string     |                                |
| phone_number  | string     | null: false                    |
| buyer         | references | null: false, foreign_key: true |

### Association
- belongs_to :buyer
- belongs_to_active_hash :prefecture