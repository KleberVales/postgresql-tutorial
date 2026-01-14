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



