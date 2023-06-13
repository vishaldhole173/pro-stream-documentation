# Table Name: breakouts

| Field            | Type          | Null | Key | Default | Extra          |
|------------------|---------------|------|-----|---------|----------------|
| id               | int           | NO   | PRI | NULL    | auto_increment |
| name             | varchar(255)  | NO   |     | NULL    |                |
| description      | text          | YES  |     | NULL    |                |
| tags             | varchar(2048) | YES  |     | NULL    |                |
| whitelist_ip     | varchar(50)   | YES  |     | NULL    |                |
| start_time       | datetime      | YES  |     | NULL    |                |
| duration_in_mins | int           | YES  |     | NULL    |                |
| event_id         | int           | NO   | MUL | NULL    |                |
| input_id         | int           | YES  | MUL | NULL    |                |
| channel_id       | int           | YES  | MUL | NULL    |                |
| status           | varchar(50)   | YES  |     | NULL    |                |
| user_id          | int           | YES  |     | NULL    |                |
| path_id          | varchar(128)  | YES  |     | NULL    |                |
| file             | varchar(2048) | YES  |     | NULL    |                |
| live             | tinyint(1)    | YES  |     | 0       |                |
| published        | tinyint(1)    | YES  |     | 0       |                |
| picture          | varchar(1024) | YES  |     | NULL    |                |
| amount           | double        | YES  |     | 0       |                |
| create_timestamp | datetime      | YES  |     | NULL    |                |
| update_timestamp | datetime      | YES  |     | NULL    |                |
| moderated        | tinyint(1)    | YES  |     | 0       |                |