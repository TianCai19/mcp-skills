---
name: database-manager
description: Manage databases across multiple types (PostgreSQL, MySQL, SQLite, MongoDB). Execute queries, create migrations, backup and restore data, import/export CSV/JSON. Use when working with databases, SQL queries, data migration, or database operations.
allowed-tools: Bash, Read, Grep, Glob
---

# Database Manager

Universal database management tool supporting multiple database types with migration, backup, and data operations.

## What this Skill does

- Execute SQL queries across multiple database types
- Create and manage database migrations
- Automated backup and restore operations
- Import/export data from CSV, JSON, SQL files
- Database health monitoring and diagnostics
- Query optimization suggestions
- Generate database documentation
- Transaction management with rollback support

## Supported Databases

- PostgreSQL
- MySQL / MariaDB
- SQLite
- MongoDB (NoSQL)

## Requirements

Install required packages:
```bash
# For SQL databases
pip install sqlalchemy psycopg2-binary mysql-connector-python

# For MongoDB
pip install pymongo

# For migrations
pip install alembic
```

Set environment variables:
```bash
export DATABASE_URL="postgresql://user:pass@localhost/dbname"
export DB_BACKUP_DIR="/path/to/backups"
```

## How to use

### Execute SQL query
```python
import os
from sqlalchemy import create_engine, text

engine = create_engine(os.getenv('DATABASE_URL'))

with engine.connect() as conn:
    result = conn.execute(text("SELECT * FROM users WHERE active = true"))
    for row in result:
        print(row)
```

### Create migration
```bash
# Initialize migration environment
alembic init migrations

# Create new migration
alembic revision --autogenerate -m "Add user table"

# Apply migrations
alembic upgrade head
```

### Backup database
```bash
# PostgreSQL
pg_dump $DATABASE_URL > backup_$(date +%Y%m%d).sql

# MySQL
mysqldump -u $DB_USER -p$DB_PASS $DB_NAME > backup_$(date +%Y%m%d).sql

# SQLite
sqlite3 database.db ".backup backup_$(date +%Y%m%d).db"
```

### Import CSV data
```python
import pandas as pd
from sqlalchemy import create_engine

df = pd.read_csv('data.csv')
engine = create_engine(os.getenv('DATABASE_URL'))
df.to_sql('table_name', engine, if_exists='append', index=False)
```

### MongoDB operations
```python
from pymongo import MongoClient

client = MongoClient(os.getenv('MONGODB_URL', 'mongodb://localhost:27017'))
db = client['mydb']
collection = db['documents']

# Insert document
result = collection.insert_one({'name': 'John', 'age': 30})

# Query documents
documents = collection.find({'age': {'$gt': 25}})
```

## Examples

When to use this Skill:
- "Create a migration to add a new table"
- "Backup the production database"
- "Import CSV data into a table"
- "Execute a complex SQL query"
- "Monitor database performance"
- "Restore data from a backup file"

## Tips

- Always backup before major operations
- Use transactions for multi-step operations
- Index frequently queried columns
- Monitor query performance
- Use connection pooling for production
