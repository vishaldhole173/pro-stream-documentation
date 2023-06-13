# Table Name: inputs

| Field                | Type         | Null | Key | Default | Extra          |
|----------------------|--------------|------|-----|---------|----------------|
| id                   | int          | NO   | PRI | NULL    | auto_increment |
| channel_id           | int          | NO   | MUL | NULL    |                |
| aws_sec_group_id     | varchar(50)  | YES  |     | NULL    |                |
| aws_input_id         | varchar(50)  | YES  |     | NULL    |                |
| aws_input_status     | varchar(50)  | YES  |     | NULL    |                |
| aws_input_dest_url_1 | varchar(255) | YES  |     | NULL    |                |
| aws_input_dest_url_2 | varchar(255) | YES  |     | NULL    |                |
| aws_input_type       | varchar(50)  | YES  |     | NULL    |                |
| create_timestamp     | timestamp    | YES  |     | NULL    |                |
| update_timestamp     | timestamp    | YES  |     | NULL    |                |
| stream_key           | varchar(255) | YES  |     | NULL    |                |