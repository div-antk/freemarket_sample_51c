# DB設計

## ★ users

| Column            | Type      | Option                        |
| ----------------- | --------- | ----------------------------- |
| nickname          | VARCHAR   | null: false                   |
| email             | VARCHAR   | null: false                   |
| password          | VARCHAR   | null: false                   |
| tel               | INT       | null: false                   |
| first_name        | VARCHAR   | null: false                   |
| last_name         | VARCHAR   | null: false                   |
| first_name_kana   | VARCHAR   | null: false                   |
| last_name_kana    | INT       | null: false                   |
| birth_year        | INT       | null: false                   |
| birth_month       | INT       | null: false                   |
| birth_day         | INT       | null: false                   |
| postal_code       | INT       | null: false                   |
| city              | VARCHAR   | null: false                   |
| street            | VARCHAR   | null: false                   |
| building_name     | VARCHAR   | null: true                    |
| credit_card       | REFERENCE | null: true, foreign_key: true |
| self_introduction | VARCHAR   | null: true                    |
| image             | VARCHAR   | null: true                    |
| rating            | REFERENCE | null: true, foreign_key: true |
| status            | INT       | null: false                   |
|                   |           |                               |

Association

- has_many :items
- has_many :comments
- has_many :likes
- has_many :ratings
- has_many :deposits
- has_one :credit_card

---

## ★ credit_cards

| Column        | Type      | Option                         |
| ------------- | --------- | ------------------------------ |
| user_id       | REFERENCE | null: false, foreign_key: true |
| number        | VARCHAR   | null: false                    |
| expiration_mm | INT       | null: false                    |
| expiration_yy | INT       | null: false                    |
| security_code | INT       | null: false                    |
|               |           |                                |

Association

- belongs_to :user

---

## ★ ratings

| Column    | Type      | Option                         |
| --------- | --------- | ------------------------------ |
| user_id   | REFERENCE | null: false, foreign_key: true |
| excellent | INT       | null: true                     |
| good      | INT       | null: true                     |
| bad       | INT       | null: true                     |
| text      | VARCHAR   | null: true                     |
|           |           |                                |

Association

- belongs_to :user
- has_many :items

---

## ★ deposits

| Column  | Type      | Option                         |
| ------- | --------- | ------------------------------ |
| user_id | REFERENCE | null: false, foreign_key: true |
| cash    | REFERENCE | null: true, foreign_key: true  |
| point   | REFERENCE | null: ture, foreign_key: true  |
|         |           |                                |

Association

- belongs_to :user

---

## ★ items

| Column      | Type      | Option                         |
| ----------- | --------- | ------------------------------ |
| user_id     | REFERENCE | null: false, foreign_key: true |
| name        | VARCHAR   | null: false                    |
| price       | INT       | null: false                    |
| image       | VARCHAR   | null: false                    |
| category    | REFERENCE | null: false, foreign_key: true |
| brand       | REFERENCE | null: true, foreign_key: true  |
| condition   | INT       | null: false                    |
| size        | INT       | null: false                    |
| description | VARCHAR   | null: false                    |
| like        | INT       | null: true                     |
| shipping    | REFERENCE | null: false, foreign_key: true |
| user_id     | REFERENCE | null: false, foreign_key: true |
|             |           |                                |

Association

- belongs_to :user
- has_many: comments
- has_many: images
- has_many: likes
- has_one: category
- has_one: brand, thorough: :category
- has_one: shipping

---

## ★ shippings

| Column        | Type      | Option                         |
| ------------- | --------- | ------------------------------ |
| item_id       | REFERENCE | null: false, foreign_key: true |
| cost          | INT       | null: false                    |
| service       | INT       | null: false                    |
| handling_time | INT       | null: false                    |
|               |           |                                |

Association

- belongs_to :item

---

## ★ categories

| Column    | Type      | Option                         |
| --------- | --------- | ------------------------------ |
| parent_id | REFERENCE | null: false, foreign_key: true |
| category  | VARCHAR   | null: false                    |
| brand_id  | REFERENCE | null: true, foreign_key: true  |
|           |           |                                |

Association

- belongs_to :item
- has_one :brands

---

## ★ brands

| Column      | Type    | Option      |
| ----------- | ------- | ----------- |
| category_id | INT     | null: false |
| name        | VARCHAR | null: false |
|             |         |             |

Association

- belongs_to :category

---

## ★ comments

| Column  | Type      | Option                         |
| ------- | --------- | ------------------------------ |
| user_id | REFERENCE | null: false, foreign_key: true |
| item_id | REFERENCE | null: false, foreign_key: true |
| comment | VARCHAR   | null: false                    |
|         |           |                                |

Association

- belongs_to :user
- belongs_to :item

---

## ★ images

| Column  | Type      | Option                         |
| ------- | --------- | ------------------------------ |
| user_id | REFERENCE | null: false, foreign_key: true |
| item_id | REFERENCE | null: false, foreign_key: true |
| image   | VARCHAR   | null: false                    |
|         |           |                                |

Association

- belongs_to :user

---

## ★ likes

| Column  | Type      | Option                         |
| ------- | --------- | ------------------------------ |
| user_id | REFERENCE | null: false, foreign_key: true |
| item_id | REFERENCE | null: false, foreign_key: true |
|         |           |                                |

Association

- belongs_to :user
- belongs_to :item

---
