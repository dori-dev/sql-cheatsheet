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

<br>

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

<br>

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

<br>
