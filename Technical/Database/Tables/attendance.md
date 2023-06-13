
# Table Name: attendance

| Field            | Type          | Null | Key | Default                                          | Extra          |
|------------------|---------------|------|-----|--------------------------------------------------|----------------|
| id               | int           | NO   | PRI | NULL                                             | auto_increment |
| user_id          | int           | NO   | UNI | NULL                                             |                |
| breakout_id      | int           | NO   | UNI | NULL                                             |                |
| session_id       | varchar(10)   | NO   | UNI | NULL                                             |                |
| entry_timestamp  | timestamp     | NO   |     | NULL                                             |                |
| exit_timestamp   | timestamp     | YES  |     | NULL                                             |                |
| city             | varchar(30)   | YES  |     | NULL                                             |                |
| region           | varchar(30)   | YES  |     | NULL                                             |                |
| country_code     | varchar(3)    | YES  |     | NULL                                             |                |
| latitude         | decimal(10,6) | YES  |     | NULL                                             |                |
| longitude        | decimal(10,6) | YES  |     | NULL                                             |                |
| type             | varchar(10)   | NO   |     | LIVE                                             |                |
| browser          | varchar(20)   | YES  |     | NULL                                             |                |
| browser_version  | varchar(20)   | YES  |     | NULL                                             |                |
| user_agent       | TEXT          | YES  |     | NULL                                             |                |
| os               | varchar(20)   | YES  |     | NULL                                             |                |
| platform         | varchar(20)   | YES  |     | NULL                                             |                |
| create_timestamp | datetime      | NO   |     | CURRENT_TIMESTAMP                                |                |
| update_timestamp | datetime      | NO   |     | CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP    |                |
