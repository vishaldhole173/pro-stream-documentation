# Table Name: users

| Field             | Type         | Null | Key | Default           | Extra             |
|-------------------|--------------|------|-----|-------------------|-------------------|
| id                | int          | NO   | PRI | NULL              | auto_increment    |
| authentication_id | varchar(255) | NO   | UNI | NULL              |                   |
| full_name         | varchar(64)  | NO   |     | NULL              |                   |
| email             | varchar(64)  | NO   |     | NULL              |                   |
| provider          | varchar(64)  | NO   |     | NULL              |                   |
| active            | tinyint(1)   | YES  |     | 1                 |                   |
| admin             | tinyint(1)   | YES  |     | 0                 |                   |
| created           | datetime     | NO   |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED |
| modified          | datetime     | NO   |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED |
| last_seen         | datetime     | NO   |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED |
| path_id           | varchar(128) | YES  |     | NULL              |                   |
| moderator         | tinyint(1)   | YES  |     | 0                 |                   |
