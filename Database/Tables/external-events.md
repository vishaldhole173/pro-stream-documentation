# Table Name: external-events

| Field                | Type          | Null | Key | Default           | Extra             |
|----------------------|---------------|------|-----|-------------------|-------------------|
| id                   | int           | NO   | PRI | NULL              | auto_increment    |
| nav_background_color | varchar(7)    | NO   |     | NULL              |                   |
| nav_logo_file_name   | varchar(64)   | NO   |     | NULL              |                   |
| created              | datetime      | NO   |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED |
| modified             | datetime      | NO   |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED |
| redirect             | varchar(1028) | YES  |     | NULL              |                   |
| client_id            | varchar(36)   | NO   |     | NULL              |                   |
