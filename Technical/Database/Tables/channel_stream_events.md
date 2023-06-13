| Field            | Type          | Null | Key | Default                 | Extra          |
|------------------|---------------|------|-----|----------------------|----------------|
| id               | int           | NO   | PRI |                      | auto_increment |
| event_name       | varchar(64)   | NO   |     |                      |                |
| event_type       | varchar(48)   | NO   |     |                      |                |
| channel_id       | int           | YES  | MUL | NULL                 |                |
| breakout_id      | int           | YES  | MUL | NULL                 |                |
| event_details    | text          | YES  |     | NULL                 |                |
| create_timestamp | datetime(3)   | NO   |     | CURRENT_TIMESTAMP(3) |                |
