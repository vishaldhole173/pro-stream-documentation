# Table Name: events

| Field       | Type          | Null | Key | Default | Extra          |
|-------------|---------------|------|-----|---------|----------------|
| id          | int           | NO   | PRI | NULL    | auto_increment |
| user_id     | int           | NO   |     | NULL    |                |
| created     | datetime      | YES  |     | NULL    |                |
| title       | varchar(64)   | YES  |     | NULL    |                |
| start_time  | datetime      | YES  |     | NULL    |                |
| end_time    | datetime      | YES  |     | NULL    |                |
| venue       | varchar(64)   | YES  |     | NULL    |                |
| type        | varchar(64)   | YES  |     | NULL    |                |
| location    | varchar(64)   | YES  |     | NULL    |                |
| description | text          | YES  |     | NULL    |                |
| month_year  | varchar(32)   | YES  |     | NULL    |                |
| published   | tinyint       | YES  |     | NULL    |                |
| path_id     | varchar(128)  | YES  |     | NULL    |                |
| picture     | varchar(1024) | YES  |     | NULL    |                |
| tenant      | varchar(128)  | YES  | UNI | NULL    |                |
