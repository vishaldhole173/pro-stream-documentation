# Table Name: survey

| Field            | Type         | Null | Key | Default | Extra          |
|------------------|--------------|------|-----|---------|----------------|
| id               | int          | NO   | PRI | NULL    | auto_increment |
| name             | varchar(255) | NO   |     | NULL    |                |
| user_id          | int          | YES  | MUL | NULL    |                |
| breakout_id      | int          | YES  | MUL | NULL    |                |
| question         | json         | YES  |     | NULL    |                |
| create_timestamp | timestamp    | YES  |     | NULL    |                |
| update_timestamp | timestamp    | YES  |     | NULL    |                |
