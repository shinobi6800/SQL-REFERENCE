# Getting Started with SQL

## Introduction
SQL (**Structured Query Language**) is used to interact with relational databases. This guide covers the basics, including database creation, CRUD operations, filtering, joins, and advanced concepts.

## Prerequisites
To use SQL, install a database system like:
- **MySQL**: `sudo pacman -S mysql`
- **PostgreSQL**: `sudo pacman -S postgresql`
- **SQLite** (lightweight, no setup needed)

Start MySQL:
```sh
sudo systemctl start mysqld
```

## 1. Creating a Database & Table
```sql
CREATE DATABASE mydatabase;
USE mydatabase;

CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    age INT,
    email VARCHAR(100) UNIQUE
);
```

## 2. CRUD Operations
### Insert Data
```sql
INSERT INTO users (name, age, email)
VALUES ('John Doe', 25, 'john@example.com');
```

### Read Data
```sql
SELECT * FROM users;
SELECT name, age FROM users WHERE age > 20;
```

### Update Data
```sql
UPDATE users SET age = 26 WHERE name = 'John Doe';
```

### Delete Data
```sql
DELETE FROM users WHERE name = 'John Doe';
```

## 3. Filtering, Sorting, & Aggregation
### Filtering with `WHERE`
```sql
SELECT * FROM users WHERE age >= 25;
```

### Sorting (`ORDER BY`)
```sql
SELECT * FROM users ORDER BY age DESC;
```

### Counting Rows
```sql
SELECT COUNT(*) FROM users;
```

### Grouping (`GROUP BY`)
```sql
SELECT age, COUNT(*) FROM users GROUP BY age;
```

## 4. Relationships & Joins
### Foreign Key (One-to-Many)
```sql
CREATE TABLE orders (
    id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT,
    product VARCHAR(100),
    FOREIGN KEY (user_id) REFERENCES users(id)
);
```

### Joining Tables (`INNER JOIN`)
```sql
SELECT users.name, orders.product
FROM users
INNER JOIN orders ON users.id = orders.user_id;
```

## 5. Advanced Concepts
### Indexes (Faster Searches)
```sql
CREATE INDEX idx_email ON users(email);
```

### Views (Virtual Tables)
```sql
CREATE VIEW user_orders AS
SELECT users.name, orders.product
FROM users INNER JOIN orders ON users.id = orders.user_id;
```

### Transactions (Safe Updates)
```sql
START TRANSACTION;
UPDATE users SET age = 30 WHERE name = 'John Doe';
ROLLBACK; -- Undo changes
COMMIT;  -- Save changes
```

## Next Steps
- Practice SQL using [DB Fiddle](https://dbfiddle.uk/)
- Learn about **stored procedures & triggers**
- Try using **PostgreSQL or SQLite** for projects

Happy coding! 🚀

