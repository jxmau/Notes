This sheet assembles main SQL command line.

# Create a database

```SQL
CREATE DATABASE database_name;
```

# SELECT a table

```SQL

-- To see all
SELECT * FROM table_name;

--To see only some columns
SELECT (column1, column2) FROM table_name;

```

# Delete a table

```SQL

DROP TABLE table;

```

# Alter a table

```SQL 

--Rename a column
ALTER TABLE table_name 
RENAME COLUMN column_name TO new_column_name;

```

# Update value in table

```SQL

UPDATE table_name
SET coumn_name = REPLACE (column, old_value, new_value);

```

# Where statements

```SQL

--Simple condition
SELECT * FROM table_name
WHERE name_column = 'name';

--Multiple conditions 
SELECT * FROM table_name
WHERE name_column = 'name' OR name_column = 'other name';

```