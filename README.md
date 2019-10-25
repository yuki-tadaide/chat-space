# README


### groups_usersテーブル 
<!-- 中間テーブル -->
  |Column|Type|Options|
  |------|----|-------|
  |user_id|integer|null: false, foreign_key: true|
  |group_id|integer|null: false, foreign_key: true|

  ### Association
  - belongs_to : group
    belongs_to : user

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
<!-- グループ作成テーブル。外部キー：id -->
  |Column|Type|Options|
  |------|----|-------|
  |name|string|null: false, unique: true|

  ### Association
    has_many : massages
    has_many : groups_users
    has_many :users, through: :groups_users
### messagesテーブル
<!-- メッセージ投稿機能。外部キー：user_id,,group_id -->
  |Column|Type|Options|
  |------|----|-------|
  |group_id|integer|null: false, foreign_key: true|
  |user_id|integer|null: false, foreign_key: true|
  |message|string|
  |image|string|

  ### Association
  - belongs_to : user
  - belongs_to : group
