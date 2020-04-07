# DB設計
## usersテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|index: true, null: false|
|mail|string|null: false, unique: true|
|password|string|null: false|

### Association
- has_many :groups, through: groups_users
- has_many :messages


## groupsテーブル

|Column|Type|Options|
|------|----|------|
|name|string|null: false|
|member|string|null: false|

### Association
- has_many :users, through: groups_users
- has_many :messages


## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|text|text||
|image|text||
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group


## users_groupsテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group