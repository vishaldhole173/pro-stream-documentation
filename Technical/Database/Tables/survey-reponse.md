# Table Name: survey-reponse

| Field            | Type      | Null | Key | Default | Extra          |
|------------------|-----------|------|-----|---------|----------------|
| id               | int       | NO   | PRI | NULL    | auto_increment |
| survey_id        | int       | NO   | MUL | NULL    |                |
| user_id          | int       | NO   | MUL | NULL    |                |
| response         | json      | NO   |     | NULL    |                |
| create_timestamp | timestamp | YES  |     | NULL    |                |
| update_timestamp | timestamp | YES  |     | NULL    |                |
