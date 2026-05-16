# ⭐ Am I Famous?

Am I Famous is a web application that allows users to check if their email address appears in a data breach. 

It is inspired by [Have I Been Pwned](https://haveibeenpwned.com/) service and was built for scratch as a learning project on backend PHP development.

## ⚠️ Disclaimer

This project was made for educational purposes only. I do not endorse or support sharing/having of personal data that does not belong to you.

## Setup

### Project

* Git clone repo:

```bash
git clone https://github.com/edveikis/AmIFamous.git
```

* cd into it

```bash
cd AmIFamous/
```

* composer install

* docker compose up

### Database

#### Create tables

* breaches:

```sql
CREATE TABLE breaches (
    id INT NOT NULL AUTO_INCREMENT,
    name VARCHAR(255),
    file_name VARCHAR(255),
    line_count INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,

    PRIMARY KEY (id)
);
```

* breach_records:

```sql
CREATE TABLE breach_data (
    id INT NOT NULL AUTO_INCREMENT,
    breach_id INT NOT NULL,

    email VARCHAR(255),
    username VARCHAR(255),
    password VARCHAR(255),

    raw_data JSON,

    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,

    PRIMARY KEY (id),

    INDEX idx_breach_id (breach_id),

    CONSTRAINT fk_breach_data_breach
        FOREIGN KEY (breach_id)
        REFERENCES breaches(id)
        ON DELETE CASCADE
        ON UPDATE CASCADE
);
```

#### default config/db.php file

```php
<?php

return [
    'host' => 'db',
    'port' => '3306',
    'dbname' => 'amifamous',
    'username' => 'admin',
    'password' => 'password'
];
```

### Open it in a browser

* Open `http://localhost:8080/` in your browser
