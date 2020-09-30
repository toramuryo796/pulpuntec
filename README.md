# README

## users(管理者)

| Column   |Type    | Options     |
| -------- |------- | ----------- |
| name     |string  | null: false |
| password |integer | null: false |

### Association
has_many :article

## articles（記事）

| Column       | Type        | Options                        |
| ------------ | ----------- | ------------------------------ |
| title        | string      | null: false                    |
| content      | text        | null: false                    |
| user         | references  | null: false, foreign_key: true |

### Association
belongs_to :user
has_many :article_tags
has_many :tags, through: :article_tags

## tags(記事のタグ)

| Column       | Type      | Options                       |
| ------------ | --------- | ----------------------------- |
| name         | string    | null: false, uniqueness: true |

### Association
has_many :article_tags
has_many : article, through: :article_tags

## article_tags(中間テーブル)

| Column   | Type       | Options                        |
| -------- | ---------  | -----------------------------  |
| article  | references | null: false, foreign_key: true |
| tag      | references | null: false, foreign_key: true |

### Association
belongs_to : article
belongs_to : tag

