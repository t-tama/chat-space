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

* Deployment instructions

* ...

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|PK: true, null: false|
|user_name|string|PK: true, null: false|
|e-mail|string|null: false , unique: true|
|password|string|null :false, null: false|
|created_dt|timestamp| 

### Association
has_many :groups_users
has_many :groups, through: :groups_users
has_many :messages


## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|group_id|integer|PK: true , null: false|
|group_name|string|PK: true ,null: false|
|created_dt|timestamp|

### Association
has_many :groups_users
has_many :users, through: :groups_users
has_many :messages

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|PK: true, null: false, foreign_key: true|
|group_id|integer|PK: true,null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user


## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|message_id|integer|PK: true , null: false|
|body|string|null: false|
|image|string|null: true|
|group_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|
|created_dt|timestamp|

### Association
- belongs_to :group
- belongs_to :user
