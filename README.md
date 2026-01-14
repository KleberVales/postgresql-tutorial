# postgresql-tutorial

## What is PostgreSQL?

PostgreSQL is an open-source, object-relational database management system (ORDBMS) known for performance, reliability, extensibility, and SQL compliance.

## 🗄️ Core Concepts

### Databases & Schemas
- Database: Logical container for data.
- Schema: Namespace to organize database objects.
- Default schema: public

## 📊 Data Types
- Numeric: INTEGER, BIGINT, SERIAL, NUMERIC, FLOAT
- Character: VARCHAR(n), CHAR(n), TEXT
- Date/Time: DATE, TIME, TIMESTAMP, INTERVAL
- Boolean: BOOLEAN
- UUID
- JSON / JSONB
- ARRAY

## 🧱 Tables & Constraints

### Table Creation

```sql

CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  name VARCHAR(100) NOT NULL,
  email VARCHAR(150) UNIQUE,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);


```

### Constraints

- PRIMARY KEY
- FOREIGN KEY
- UNIQUE
- NOT NULL
- CHECK
- DEFAULT

## 🔗 Relationships

- One-to-One
- One-to-Many
- Many-to-Many (junction table)

```sql
FOREIGN KEY (user_id) REFERENCES users(id)
```

## 🔍 Queries (DML)

### Basic Commands

```sql
SELECT * FROM users;
INSERT INTO users (name, email) VALUES ('Kleber', 'k@email.com');
UPDATE users SET name = 'New Name' WHERE id = 1;
DELETE FROM users WHERE id = 1;
```

### Filtering & Ordering

- WHERE, AND, OR
- ORDER BY
- LIMIT, OFFSET
- LIKE, ILIKE
- IN, BETWEEN

## 📐 Joins

- INNER JOIN
- LEFT JOIN
- RIGHT JOIN
- FULL JOIN

```sql
SELECT u.name, o.total
FROM users u
INNER JOIN orders o ON u.id = o.user_id;
```

## 📈 Aggregations

- COUNT, SUM, AVG, MIN, MAX
- GROUP BY
- HAVING

## ⚡ Indexes

Improve query performance:

```sql
CREATE INDEX idx_users_email ON users(email);
```

- Types:

    - B-tree (default)

    - Hash

    - GIN / GiST (JSON, full-text search)
 
## 🔐 Transactions

- ACID compliant

```sql
BEGIN;
UPDATE accounts SET balance = balance - 100 WHERE id = 1;
UPDATE accounts SET balance = balance + 100 WHERE id = 2;
COMMIT;
```

- ROLLBACK to cancel

## 🔒 Security & Roles

- Roles = users + permissions

```sql
CREATE ROLE app_user LOGIN PASSWORD '123';
GRANT SELECT, INSERT ON users TO app_user;
```

## ⚙️ Views & Functions

- View: Stored query

```sql

CREATE VIEW active_users AS
SELECT * FROM users WHERE active = true;

```

- Functions (PL/pgSQL)

```sql

CREATE FUNCTION get_user_count()
RETURNS INTEGER AS $$
BEGIN
  RETURN (SELECT COUNT(*) FROM users);
END;
$$ LANGUAGE plpgsql;

```

## 📦 Backup & Restore

- Backup: pg_dump

- Restore: pg_restore

- Full cluster: pg_dumpall

