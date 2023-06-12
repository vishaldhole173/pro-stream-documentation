# Table Name: distributions

| Field                    | Type         | Null | Key | Default | Extra          |
|--------------------------|--------------|------|-----|---------|----------------|
| id                       | int          | NO   | PRI | NULL    | auto_increment |
| breakout_id              | int          | NO   |     | NULL    |                |
| aws_distribution_id      | varchar(50)  | YES  |     | NULL    |                |
| aws_distribution_domain  | varchar(255) | YES  |     | NULL    |                |
| endpoint_url             | varchar(255) | YES  |     | NULL    |                |
| status                   | varchar(25)  | YES  |     | NULL    |                |
| price_class              | varchar(25)  | YES  |     | NULL    |                |
| create_timestamp         | timestamp    | YES  |     | NULL    |                |
| update_timestamp         | timestamp    | YES  |     | NULL    |                |
| active                   | tinyint(1)   | YES  |     | 1       |                |
| metrics_bytes_downloaded | bigint       | NO   |     | 0       |                |
| deleted                  | tinyint(1)   | NO   |     | 0       |                |
