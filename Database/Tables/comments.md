# Table Name: comments

| Field            | Type         | Null | Key | Default | Extra          |
|------------------|--------------|------|-----|---------|----------------|
| id               | int          | NO   | PRI | NULL    | auto_increment |
| user_name        | varchar(255) | NO   |     | NULL    |                |
| message          | text         | YES  |     | NULL    |                |
| create_timestamp | timestamp    | YES  |     | NULL    |                |
| breakout_id      | int          | NO   | MUL | NULL    |                |
| user_id          | int          | NO   | MUL | NULL    |                |
| moderator        | tinyint(1)   | YES  |     | 0       |                |
| published        | tinyint(1)   | YES  |     | 0       |                |
