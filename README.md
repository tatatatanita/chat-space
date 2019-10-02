# 開発環境
- Ruby 2.5.1
- Rails 5.2.3

# DB設計
## usersテーブル

|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|nickname|string|null: false|

### Association
- has_many :groups
- has_many :messages
- has_many :groups_users
- has_many groups through: :group_users


## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|body|text| |
|image|string| |
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group


## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|group_name|string|null: false, unique: true|

### Association
- has_many :users
- has_many :messages
- has_many :groups_users
- belongs_to users through: :group_users


## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group