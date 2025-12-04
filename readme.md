 Readme.md

This project contains a simple HTML form and a PHP backend that stores customer data into a MySQL database.

 Features
- HTML form with Name, Email, Message fields  
- PHP backend (`submit.php`)  
- Stores data in MySQL database  
- Ready for deployment on Debian  
- Supports ngrok for public testing

---

Files
- `index.html`
A customer form that sends data to `submit.php`.

- `submit.php`
Processes POST data and inserts it into the MySQL database:
- Table: `customers`
- Columns: `id`, `name`, `email`, `message`

---

 Database Setup (MySQL)

Run these commands on your MySQL server:

```sql
CREATE DATABASE customer_db;

CREATE USER 'webuser'@'localhost' IDENTIFIED BY 'password123';

GRANT ALL PRIVILEGES ON customer_db.* TO 'webuser'@'localhost';

USE customer_db;

CREATE TABLE customers (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100),
  email VARCHAR(100),
  message TEXT
);
```

---

  Debian Server Setup

Install Apache, PHP, MySQL:

```sh
sudo apt update
sudo apt install apache2 php php-mysqli mysql-server -y
```

Move your project files to the web directory:

```sh
sudo cp index.html /var/www/html/
sudo cp submit.php /var/www/html/
```

Restart Apache:

```sh
sudo systemctl restart apache2
```

---

  ngrok for Public Access

Install ngrok and expose Apache:

```sh
ngrok http 80
```

You will get a public URL like:

```
https://abcd1234.ngrok-free.app
```

Use this link to access your form from anywhere.

---

** Finished
Your form is now online, connected to a database, and accessible through ngrok.

