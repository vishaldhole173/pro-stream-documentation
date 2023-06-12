# Table Name: recordings

| Field                | Type         | Null | Key | Default | Extra          |
|----------------------|--------------|------|-----|---------|----------------|
| id                   | int          | NO   | PRI | NULL    | auto_increment |
| breakout_id          | int          | NO   |     | NULL    |                |
| media_convert_job_id | varchar(32)  | NO   |     | NULL    |                |
| job_status           | varchar(16)  | NO   |     | NULL    |                |
| recording_path       | varchar(255) | YES  |     | NULL    |                |
| create_timestamp     | timestamp    | YES  |     | NULL    |                |
| update_timestamp     | timestamp    | YES  |     | NULL    |                |
