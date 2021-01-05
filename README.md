## usersテーブル

|Column    |Type     |Option      |
|----------|---------|------------|
|nickname  |string   |null: false |
|email     |string   |null: false |
|password  |string   |null: false |
|birthday  |integer  |null: false |


### Association
-has_many :articles
-has_many :comments
-has_many :room_users
-has_many :rooms, through: room_users
-has_many :messages


## roomsテーブル

|Column |Type   |Option      |
|-------|-------|------------|
|name   |string |null: false |


### Association
-has_many :room_users
-has_many :users, through: room_users
-has_many :messages


## room_usersテーブル

|Column|Type       |Option                         |
|------|-----------|-------------------------------|
|user  |references |null: false, foreign_key: true |
|room  |references |null: false, foreign_key: true |


### Association
-belongs_to :room
-belongs_to :user


## messagesテーブル

|Column  |Type       |Option                         |
|--------|-----------|-------------------------------|
|user    |references |null: false, foreign_key: true |
|room    |references |null: false, foreign_key: true |
|content |string     |                               |


### Association
-belongs_to :room
-belongs_to :user


## articlesテーブル

|Column  |Type       |Option                         |
|--------|-----------|-------------------------------|
|user    |references |null: false, foreign_key: true |
|title   |string     |null: false                    |
|content |string     |null: false                    |


### Association
-belongs_to :user
-has_many :comments


## commentsテーブル

|Column   |Type       |Option                         |
|---------|-----------|-------------------------------|
|user     |references |null: false, foreign_key: true |
|article  |references |null: false, foreign_key: true |
|content  |string     |                               |


### Association
-belongs_to :user
-belongs_to :article



