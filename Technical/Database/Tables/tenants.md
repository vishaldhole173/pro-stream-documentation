| Field            | Type          | Null | Key | Default                 | Extra          |
|------------------|---------------|------|-----|----------------------|----------------|
| id               | int           | NO   | PRI |                      | auto_increment |
| name             | varchar(128)  | NO   |     |                      |                |
| sub_domain_name  | varchar(48)   | NO   |     |                      |                |
| event_path_id    | varchar(15)   | YES  |     | NULL                 |                |
| redirect_url     | VARCHAR(1024) | YES  |     | '/calendar'          |                |
| admin_password   | VARCHAR(256)  | NO   |     |                      |                |
| logo             | VARCHAR(64)   | NO   |     |                      |                |
| background_color | VARCHAR(7)    | NO   |     |                      |                |
| website          | VARCHAR(1024) | YES  |     | NULL                 |                |
| twitter          | VARCHAR(1024) | YES  |     | NULL                 |                |
| facebook         | VARCHAR(1024) | YES  |     | NULL                 |                |
| instagram        | VARCHAR(1024) | YES  |     | NULL                 |                |
| create_timestamp | datetime(3)   | NO   |     | CURRENT_TIMESTAMP(3) |                |
| update_timestamp | datetime(3)   | NO   |     | CURRENT_TIMESTAMP(3) |                |
