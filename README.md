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

## ★ credit_cards

| Column        | Type      | Option                         |
| ------------- | --------- | ------------------------------ |
| user_id       | REFERENCE | null: false, foreign_key: true |
| number        | VARCHAR   | null: false                    |
| expiration_mm | INT       | null: false                    |
| expiration_yy | INT       | null: false                    |
| security_code | INT       | null: false                    |
|               |           |                                |

## ★ rating

| Column    | Type      | Option                         |
| --------- | --------- | ------------------------------ |
| user_id   | REFERENCE | null: false, foreign_key: true |
| excellent | INT       | null: true                     |
| good      | INT       | null: true                     |
| bad       | INT       | null: true                     |
|           |           |                                |

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

## ★ shippings

| Column        | Type      | Option                         |
| ------------- | --------- | ------------------------------ |
| item_id       | REFERENCE | null: false, foreign_key: true |
| cost          | INT       | null: false                    |
| service       | INT       | null: false                    |
| handling_time | INT       | null: false                    |
|               |           |                                |

## ★ categories

| Column    | Type      | Option                         |
| --------- | --------- | ------------------------------ |
| parent_id | REFERENCE | null: false, foreign_key: true |
| category  | VARCHAR   | null: false                    |
| brand_id  | REFERENCE | null: true, foreign_key: true  |
|           |           |                                |

## ★ comments

| Column  | Type      | Option                         |
| ------- | --------- | ------------------------------ |
| user_id | REFERENCE | null: false, foreign_key: true |
| item_id | REFERENCE | null: false, foreign_key: true |
| comment | VARCHAR   | null: false                    |
|         |           |                                |

## ★ images

| Column  | Type      | Option                         |
| ------- | --------- | ------------------------------ |
| user_id | REFERENCE | null: false, foreign_key: true |
| item_id | REFERENCE | null: false, foreign_key: true |
| image   | VARCHAR   | null: false                    |
|         |           |                                |

## ★ deposits

| Column  | Type      | Option                         |
| ------- | --------- | ------------------------------ |
| user_id | REFERENCE | null: false, foreign_key: true |
| cash    | REFERENCE | null: true, foreign_key: true  |
| point   | REFERENCE | null: ture, foreign_key: true  |
|         |           |                                |