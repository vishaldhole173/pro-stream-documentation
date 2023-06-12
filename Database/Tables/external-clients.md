# Table Name: external-clients

| Field            | Type         | Null | Key | Default           | Extra                                         |
|------------------|--------------|------|-----|-------------------|-----------------------------------------------|
| id               | int          | NO   | PRI | NULL              | auto_increment                                |
| client_id        | varchar(36)  | NO   | UNI | NULL              |                                               |
| client_name      | varchar(255) | NO   |     | NULL              |                                               |
| client_jwt_key   | varchar(255) | YES  |     | NULL              |                                               |
| client_host      | varchar(255) | NO   |     | NULL              |                                               |
| create_timestamp | datetime     | YES  |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED                             |
| update_timestamp | datetime     | YES  |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED on update CURRENT_TIMESTAMP |
