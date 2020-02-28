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

# Chat-space DB設計

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|Name|string|null: false, unique: true|
|email|string|null: faise, unique: true|
|password|string|null: false, unique: true|

### Association
- has_many :team, through: :users_group
- has_many :messages
- has_many :users_group

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|text|null: false|
|image|string|null: false|
|team_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|

### Association
- has_many :users 
- has_many :team

## users_teamテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :team
- belongs_to :users

## teamテーブル
|Column|Type|Options|
|------|----|-------|
|team_name|string|null: false, unique: true|

### Association
- has_many: users
- has_many: messages