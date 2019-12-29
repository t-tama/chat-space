# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* ...

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_name|string|PK, null: false, index: true|
|e-mail|string|null: false , unique: true|
|password|string|null :false, null: false|

### Association
has_many :groups_users
has_many :groups, through: :groups_users
has_many :messages


## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|group_name|string|PK,null: false|

### Association
has_many :groups_users
has_many :users, through: :groups_users
has_many :messages

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|PK, null: false, foreign_key: true|
|group_id|references|PK,null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user


## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|string|
|image|string|
|group_id|references|null: false, foreign_key: true|
|user_id|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user
