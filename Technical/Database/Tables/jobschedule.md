# Table Name: jobschedule

| Field            | Type         | Null | Key | Default | Extra          |
|------------------|--------------|------|-----|---------|----------------|
| id               | int          | NO   | PRI | NULL    | auto_increment |
| name             | varchar(255) | NO   | UNI | NULL    |                |
| when             | timestamp    | NO   |     | NULL    |                |
| what             | varchar(50)  | NO   |     | NULL    |                |
| args             | varchar(255) | YES  |     | NULL    |                |
| pending          | tinyint(1)   | YES  |     | 1       |                |
| create_timestamp | timestamp    | YES  |     | NULL    |                |
| update_timestamp | timestamp    | YES  |     | NULL    |                |
