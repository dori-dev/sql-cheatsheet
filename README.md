# SQL CheatSheet

SQL cheat sheet for simple sql commands.

# Summary

- [SELECT](#select) - Select data from a table.
  <br>
- [WHERE](#where) - Add conditions on queries result.
  <br>
- [ORDER BY](#order-by) - Sort the result of values.
  <br>
- [LIKE](#like) - Filter values like a pattern.
  <br>
- [LIMIT](#limit) - Limit the number of result rows of a query.
  <br>
- [JOIN](#join) - Join the columns of several tables together.
  <br>
- [GROUP BY](#group-by) - Group the same row in column.
  <br>
- [HAVING](#having) - Use having for filter result after group by.
  <br>
- [UNION](#union) - Merge two select command.
  <br>
- [INSERT](#insert-into) - Insert a row to a table.
  <br>
- [UPDATE](#update) - Update a row or rows from table.
  <br>
- [DELETE](#delete) - Delete a row or rows from table.
  <br>
- [SELECT INTO](#select-into) - Select columns from table and insert them in another table.
  <br>
- [CREATE & DROP](#create--drop) - Create and drop a database or table.
  <br>
- [ALTER](#alter) - Change the table properties.
  <br>
- [INDEX](#index) - Add and remove index in table.
  <br>
- [CONSTRAINT](#constraint) - Add constraints to table columns.

#

## SELECT

**SELECT**: Select data from a table.

```sql
SELECT column_name
FROM table_name;
```

<br>

**SELECT \***: Select all data from a table.

```sql
SELECT * FROM table_name;
```

<br>

**DISTINCT**: Remove Duplicate values from result.

```sql
SELECT DISTINCT column1
FROM table_name;
```

<br>

**COUNT**: Show values count.

```sql
SELECT COUNT(column1)
FROM table_name;
```

<br>

**OPERATORS**: Performing calculations on values with a same data type.

```sql
SELECT column1, (column2 - column3) AS distance
FROM table_name;
```

#

## WHERE

**WHERE**: Add conditions on queries result.

```sql
SELECT column1
FROM table_name
WHERE column1 > 10;
```

<br>

**AND**: And operator.

```sql
SELECT column1
FROM table_name
WHERE column1 > 10 AND column1 < 3;
```

<br>

**OR**: Or operator.

```sql
SELECT column1
FROM table_name
WHERE column1 = 10 OR column1 = 3;
```

<br>

**NOT**: Not operator.

```sql
SELECT column1
FROM table_name
WHERE NOT column1 < 3;
```

<br>

**BETWEEN**: Select all values between x and y.

```sql
SELECT column1
FROM table_name
WHERE column1 BETWEEN 3 AND 10;
```

<br>

**IN**: Filter all values in the list.

```sql
SELECT column1
FROM table_name
WHERE column1 IN (2, 3, 10, 15);
```

#

## ORDER BY

**ASC**: Sort values in ascending order.

```sql
SELECT *
FROM table_name
ORDER BY column1 ASC;
```

<br>

**DESC**: Sort values in descending order.

```sql
SELECT *
FROM table_name
ORDER BY column1 DESC;
```

<br>

**MAX**: Return maximum value of column.

```sql
SELECT MAX(column1)
FROM table_name;
```

<br>

**MIN**: Return minimum value of column.

```sql
SELECT MIN(column1)
FROM table_name;
```

<br>

**AVG**: Return average of column values.

```sql
SELECT AVG(column1)
FROM table_name;
```

<br>

**SUM**: Return sum of column values.

```sql
SELECT SUM(column1)
FROM table_name;
```

#

## LIKE

**LIKE `%`**: Filter values that contain none or any number of characters instead of `%`.

```sql
SELECT column1
FROM table_name
WHERE column1 LIKE 'A%';
```

<br>

**LIKE `_`**: Filter values that have exactly one letter instead of `_`.

```sql
SELECT column1
FROM table_name
WHERE column1 LIKE 'A_f';
```

#

## LIMIT

**LIMIT**: Limit the number of result rows of a query.

```sql
SELECT column1
FROM table_name
LIMIT 30;
```

#

## JOIN

**INNER JOIN**: Merges several columns.

```sql
SELECT username, product, order_cost
FROM users
INNER JOIN products
    ON users.id = products.user_id
INNER JOIN orders
    ON products.id = orders.product_id;
```

<br>

**LEFT JOIN**: Merges multiple columns and returns null for values that exist in the left column but not in the right column.

```sql
SELECT username, product
FROM users
LEFT JOIN products
    ON users.id = products.user_id
```

<br>

**RIGHT JOIN**: Merges multiple columns and returns null for values that exist in the right column but not in the left column.

```sql
SELECT username, product
FROM users
RIGHT JOIN products
    ON users.id = products.user_id
```

<br>

**FULL JOIN**: Merges multiple columns and returns all column1 and column2 values, Even if they do not have corresponding values.

```sql
SELECT username, product
FROM users
FULL JOIN products
    ON users.id = products.user_id
```

<br>

**SELF JOIN**: Merge the column with itself to compare its own values.

```sql
SELECT t1.column1, t2.column1
FROM table1 t1, table1 t2
WHERE t1.column1 > t2.column1;
```

#

## GROUP BY

**GROUP BY**: Group the same row in column and return it once.

```sql
SELECT column1, COUNT(*)
FROM table_name
GROUP BY column1
```

#

## HAVING

**HAVING**: When we want add condition after `group by` use having.

```sql
SELECT
    products.name,
    SUM(products.price * order_items.product_count) AS total
FROM products
INNER JOIN orders
    ON  orders.product_id = products.id
INNER JOIN order_items
    ON order_items.order_id = orders.id
GROUP BY products.name
HAVING SUM(products.price * order_items.product_count) > 2000
ORDER BY products.name ASC
```

#

## UNION

**UNION**: Merge two select and remove same values from result.

```sql
SELECT column1 FROM table1
UNION
SELECT column1 FROM table2;
```

<br>

**UNION ALL**: Merge two select and don't remove same values from result.

```sql
SELECT column1 FROM table1
UNION ALL
SELECT column1 FROM table2;
```

#

## INSERT INTO

**INSERT INTO**: Adds a row to the end of the rows of the table, if you don't set a value for a column, it sets null for it.

```sql
INSERT INTO table_name(column1, column2, column3)
VALUES ("Mohammad", "Dori", 17)
```

#

## UPDATE

**UPDATE**: Update a row or rows with new values.

```sql
UPDATE table_name
SET column1='bob', column2=10
WHERE column1='jack';
```

#

## DELETE

**DELETE**: Delete a row or rows from table.

```sql
DELETE FROM table_name
WHERE column1=20;
```

#

## SELECT INTO

**SELECT INTO**: Backup a table columns and insert in the new table.

```sql
SELECT column1, column2
INTO new_table
FROM table_name
WHERE column1 IN ("Iran", "Spain", "Italia");
```

<br>

**INSERT INTO SELECT**: Back a table columns and insert in the available table.

```sql
INSERT INTO table2
SELECT column1, column2
FROM table1
WHERE column1 > 10;
```

#

# CREATE & DROP

**CREATE DATABASE**: Create a new database.

```sql
CREATE DATABASE db_name;
```

<br>

**DROP DATABASE**: Remove a database.

```sql
DROP DATABASE db_name;
```

<br>

**CREATE TABLE**: Create a new table. [All SQL data types](https://www.w3schools.com/sql/sql_datatypes.asp)

```sql
CREATE TABLE table_name(
    column1 DATA TYPE,
    column2 DATA TYPE,
    column3 DATA TYPE
);
```

<br>

**DROP Table**: Remove a table.

```sql
DROP TABLE table_name;
```

#

## ALTER

**RENAME COLUMN**: Rename the column.

```sql
ALTER TABLE table_name
RENAME column_old_name TO column_new_name;
```

<br>

**RENAME TABLE**: Rename the table.

```sql
ALTER TABLE table_old_name
RENAME TO table_new_name;
```

<br>

**CREATE COLUMN**: Add new column to the table.

```sql
ALTER TABLE table_name
ADD column_name DATA TYPE;
```

<br>

**DROP COLUMN**: Remove a column from the table.

```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```

<br>

**NEW DATA TYPE**: Change column data type.

```sql
ALTER TABLE table_name
ALTER COLUMN column_name
    SET DATA TYPE new_data_type;
```

#

## INDEX

**INDEX**: Index the table.

```sql
CREATE INDEX index_name
ON table_name (column_name);
```

<br>

**UNIQUE INDEX**: Uniquely index the table.

```sql
CREATE UNIQUE INDEX index_name
ON table_name (column_name);
```

<br>

**DROP INDEX**: Remove a table index.

```sql
DROP INDEX index_name;
```

#

## CONSTRAINT

**NOT NULL**: The column can't be null.

```sql
CREATE TABLE table_name(
    column1 DATA TYPE NOT NULL
);
```

<br>

**UNIQUE**: Creating a unique column, that is, only one of it can be in the table.

```sql
CREATE TABLE table_name(
    column1 DATA TYPE UNIQUE
);
```

<br>

**PRIMARY KEY**: Creating a primary key, it's unique, not null and connection point to other tables.

```sql
CREATE TABLE table_name(
    column1 DATA TYPE PRIMARY KEY
);
```

<br>

**FOREIGN KEY**: Creating a foreign key, it's connect to another table primary key.

```sql
CREATE TABLE table_name(
    column1 DATA TYPE PRIMARY KEY,
    column2 DATA TYPE,
    FOREIGN KEY (column2)
        REFERENCES other_table(primary_key_column)
);
```

<br>

**DEFAULT**: If no value is set for this column, it sets the default value for the columns. The opposite of NOT NULL.

```sql
CREATE TABLE table_name(
    column1 DATA TYPE PRIMARY KEY,
    column2 DATA TYPE DEFAULT default_value
);
```

<br>

**CHECK**: Checked the values of columns they are going to be added.

```sql
CREATE TABLE table_name(
    column1 DATA TYPE,
    column2 DATA TYPE,
    CONSTRAINT check_name CHECK (
        column2 > 30 AND
        LENGTH(column1) > 3
    )
)
```

<br>

**DROP CONSTRAINT**: Remove a check.

```sql
ALTER TABLE table_name
DROP CONSTRAINT check_name;
```
