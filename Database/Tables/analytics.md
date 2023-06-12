# Table Name: analytics

| Field            | Type      | Null | Key | Default           | Extra             |
|------------------|-----------|------|-----|-------------------|-------------------|
| id               | int       | NO   | PRI | NULL              | auto_increment    |
| key              | text      | NO   |     | NULL              |                   |
| value            | text      | NO   |     | NULL              |                   |
| breakout_id      | int       | NO   | MUL | NULL              |                   |
| create_timestamp | timestamp | NO   |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED |
| user_id          | int       | YES  | MUL | NULL              |                   |