# SQL CheatSheet

# Summary

[SELECT](#select)

#
## SELECT

**SELECT**: Select data from a table.

```sql
SELECT column_name FROM table_name;
```

<br>

**SELECT \***: Select all data from a table.

```sql
SELECT * FROM table_name;
```

<br>

**DISTINCT**: Remove Duplicate values from result.

```sql
SELECT DISTINCT column1 FROM table_name;
```

<br>

**COUNT**: Show values count.

```sql
SELECT COUNT(column1) FROM table_name;
```

<br>

**OPERATORS**: Performing calculations on values with a same data type.

```sql
SELECT column1, (column2 - column3) AS distance
FROM table_name;
```
