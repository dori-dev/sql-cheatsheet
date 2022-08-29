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

**DELETE**: Delete a row or rows.

```sql
DELETE FROM table_name
WHERE column1=20;
```
