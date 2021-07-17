# テーブル設計

## usersモデル

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| nickname           | string | null: false |
| email              | string | null: false |
| encrypted_password | string | null: false |

### Association
has_many :user_rooms
has_many :lists
has_many :messages

## rooms

| Column    | Type   | Options     |
| --------- | ------ | ----------- |
| room_name | string | null: false |

### Association
has_many :user_rooms
has_many :messages

## user_rooms

| Column    | Type      | Options                        |
| --------- | --------- | ------------------------------ |
| user      | reference | null: false, foreign_key: true |
| room      | reference | null: false, foreign_key: true |
| list      | reference | null: false, foreign_key: true |

### Association
belongs_to :user
belongs_to :room
belongs_to :list

## lists

| Column    | Type      | Options                        |
| --------- | --------- | ------------------------------ |
| user      | reference | null: false, foreign_key: true |
| num_id    | reference | null: false, foreign_key: true |
| name      | reference | null: false, foreign_key: true |

### Association
has_one :user_room
belongs_to :user