# Table Name: payments

| Field             | Type         | Null | Key | Default | Extra          |
|-------------------|--------------|------|-----|---------|----------------|
| id                | int          | NO   | PRI | NULL    | auto_increment |
| type              | varchar(32)  | YES  |     | NULL    |                |
| amount            | double       | YES  |     | NULL    |                |
| breakout_id       | int          | YES  |     | NULL    |                |
| user_id           | int          | NO   |     | NULL    |                |
| payment_intent_id | varchar(64)  | YES  |     | NULL    |                |
| message           | varchar(255) | YES  |     | NULL    |                |
| create_timestamp  | timestamp    | YES  |     | NULL    |                |
| update_timestamp  | timestamp    | YES  |     | NULL    |                |
