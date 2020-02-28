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
- has_many :teams, through: :users_groups
- has_many :messages
- has_many :users_groups

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|text||
|image|string||
|team|references|null: false, foreign_key: true|
|user|references|null: false, foreign_key: true|

### Association
- belongs_to :user 
- belongs_to :team

## users_teamテーブル
|Column|Type|Options|
|------|----|-------|
|user|references|null: false, foreign_key: true|
|team|references|null: false, foreign_key: true|

### Association
- belongs_to :team
- belongs_to :user

## teamテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique: true|

### Association
- has_many: users through: :users_groups
- has_many: users_groups 