# Table Name: channels

| Field                         | Type          | Null | Key | Default | Extra          |
|-------------------------------|---------------|------|-----|---------|----------------|
| id                            | int           | NO   | PRI | NULL    | auto_increment |
| name                          | varchar(255)  | NO   | UNI | NULL    |                |
| description                   | text          | YES  |     | NULL    |                |
| aws_media_live_channel_id     | varchar(50)   | YES  |     | NULL    |                |
| channel_state                 | varchar(50)   | YES  |     | NULL    |                |
| aws_media_package_channel_id  | varchar(50)   | YES  |     | NULL    |                |
| aws_media_package_endpoint_id | varchar(50)   | YES  |     | NULL    |                |
| playback_url                  | varchar(2048) | YES  |     | NULL    |                |
| input_type                    | varchar(25)   | YES  |     | NULL    |                |
| channel_arn                   | varchar(255)  | YES  |     | NULL    |                |
| channel_type                  | varchar(32)   | YES  |     | NULL    |                |
| create_timestamp              | timestamp     | YES  |     | NULL    |                |
| update_timestamp              | timestamp     | YES  |     | NULL    |                |
