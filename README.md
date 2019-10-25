# README


### groups_usersテーブル 
<!-- 中間テーブル -->
  |Column|Type|Options|
  |------|----|-------|
  |user_id|integer|null: false, foreign_key: true|
  |group_id|integer|null: false, foreign_key: true|

  ### Association
  - has_many : groups
    has_many : users

### usersテーブル
<!-- ユーザー登録機能。主キー：id -->
  |Column|Type|Options|
  |------|----|-------|
  |id|integer|null: false|
  |name|string|null: false|
  |mail|string|null: false|
  |password|string|null: false|

  ### Association
  - has_many : massages
    has_many : gruops_users
    has_many :groups, through: :groups_users

### groupsテーブル
<!-- グループ作成テーブル。外部キー：user_id -->
  |Column|Type|Options|
  |------|----|-------|
  |usr_id|integer|null: false, unique: true, foreign_key: true|
  |group_name|string|null: false, unique: true|
  |user_name|string|null: false, unique: true|
  |add_user_name|string|unique: true|

  ### Association
    has_many : massages
    has_many : groups_users
    has_many :users, through: :groups_users
### messagesテーブル
<!-- メッセージ投稿機能。外部キー：user_id,group_id -->
  |Column|Type|Options|
  |------|----|-------|
  |usr_id|integer|null: false, unique: true, foreign_key: true|
  |group_id|integer|null: false, foreign_key: true|
  |message|string|null: false|
  |image|string|

  ### Association
  - belongs_to : user
  - belongs_to : group
