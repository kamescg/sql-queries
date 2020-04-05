# SQL Queries Cheatsheet 



## Select

SELECT c1, c2 FROM t;
Query all rows and columns from a table

SELECT * FROM t;
Query data and filter rows with a condition

SELECT c1, c2 FROM t
WHERE condition;
Query distinct rows from a table

SELECT DISTINCT c1 FROM t
WHERE condition;
Sort the result set in ascending or descending order

SELECT c1, c2 FROM t
ORDER BY c1 ASC [DESC];
Skip offset of rows and return the next n rows

SELECT c1, c2 FROM t
ORDER BY c1 
LIMIT n OFFSET offset;
Group rows using an aggregate function

SELECT c1, aggregate(c2)
FROM t
GROUP BY c1;
Filter groups using HAVING clause

SELECT c1, aggregate(c2)
FROM t
GROUP BY c1
HAVING condition;
Querying from multiple tables
Inner join t1 and t2

SELECT c1, c2 
FROM t1
INNER JOIN t2 ON condition;
Left join t1 and t1

SELECT c1, c2 
FROM t1
LEFT JOIN t2 ON condition;
Right join t1 and t2

SELECT c1, c2 
FROM t1
RIGHT JOIN t2 ON condition;
Perform full outer join

SELECT c1, c2 
FROM t1
FULL OUTER JOIN t2 ON condition;
Produce a Cartesian product of rows in tables

SELECT c1, c2 
FROM t1
CROSS JOIN t2;
Another way to perform cross join

SELECT c1, c2 
FROM t1, t2;
Join t1 to itself using INNER JOIN clause

SELECT c1, c2
FROM t1 A
INNER JOIN t2 B ON condition;
Using SQL Operators
Combine rows from two queries

SELECT c1, c2 FROM t1
UNION [ALL]
SELECT c1, c2 FROM t2;
Return the intersection of two queries

SELECT c1, c2 FROM t1
INTERSECT
SELECT c1, c2 FROM t2;
Subtract a result set from another result set

SELECT c1, c2 FROM t1
MINUS
SELECT c1, c2 FROM t2;
Query rows using pattern matching %, _

SELECT c1, c2 FROM t1
WHERE c1 [NOT] LIKE pattern;
Query rows in a list

SELECT c1, c2 FROM t
WHERE c1 [NOT] IN value_list;
Query rows between two values

SELECT c1, c2 FROM t
WHERE  c1 BETWEEN low AND high;
Check if values in a table is NULL or not

SELECT c1, c2 FROM t
WHERE  c1 IS [NOT] NULL;
Managing tables
Create a new table with three columns

CREATE TABLE t (
     id INT PRIMARY KEY,
     name VARCHAR NOT NULL,
     price INT DEFAULT 0
);

## Drop

DROP TABLE t ;
Add a new column to the table

## Alter

ALTER TABLE t ADD column;
Drop column c from the table

ALTER TABLE t DROP COLUMN c ;
Add a constraint

ALTER TABLE t ADD constraint;
Drop a constraint

ALTER TABLE t DROP constraint;
Rename a table from t1 to t2

ALTER TABLE t1 RENAME TO t2;
Rename column c1 to c2

ALTER TABLE t1 RENAME c1 TO c2 ;
Remove all data in a table

TRUNCATE TABLE t;
Using SQL constraints
Set c1 and c2 as a primary key

## Create

CREATE TABLE t(
    c1 INT, c2 INT, c3 VARCHAR,
    PRIMARY KEY (c1,c2)
);
Set c2 column as a foreign key

CREATE TABLE t1(
    c1 INT PRIMARY KEY,  
    c2 INT,
    FOREIGN KEY (c2) REFERENCES t2(c2)
);
Make the values in c1 and c2 unique

CREATE TABLE t(
    c1 INT, c1 INT,
    UNIQUE(c2,c3)
);
Ensure c1 > 0 and values in c1 >= c2

CREATE TABLE t(
  c1 INT, c2 INT,
  CHECK(c1> 0 AND c1 >= c2)
);
Set values in c2 column not NULL

CREATE TABLE t(
     c1 INT PRIMARY KEY,
     c2 VARCHAR NOT NULL
);
Modifying Data
Insert one row into a table

INSERT INTO t(column_list)
VALUES(value_list);
Insert multiple rows into a table

INSERT INTO t(column_list)
VALUES (value_list), 
       (value_list), …;
Insert rows from t2 into t1

INSERT INTO t1(column_list)
SELECT column_list
FROM t2;
Update new value in the column c1 for all rows

UPDATE t
SET c1 = new_value;
Update values in the column c1, c2 that match the condition

UPDATE t
SET c1 = new_value, 
        c2 = new_value
WHERE condition;
Delete all data in a table

DELETE FROM t;
Delete subset of rows in a table

DELETE FROM t
WHERE condition;
Managing Views
Create a new view that consists  of c1 and c2

CREATE VIEW v(c1,c2) 
AS
SELECT c1, c2
FROM t;
Create a new view with check option

CREATE VIEW v(c1,c2) 
AS
SELECT c1, c2
FROM t;
WITH [CASCADED | LOCAL] CHECK OPTION;
Create a recursive view

CREATE RECURSIVE VIEW v 
AS
select-statement -- anchor part
UNION [ALL]
select-statement; -- recursive part
Create a temporary view

CREATE TEMPORARY VIEW v 
AS
SELECT c1, c2
FROM t;
Delete a view

DROP VIEW view_name;
Managing indexes
Create an index on c1 and c2 of the t table

CREATE INDEX idx_name 
ON t(c1,c2);
Create a unique index on c3, c4 of the t table

CREATE UNIQUE INDEX idx_name
ON t(c3,c4)
Drop an index

DROP INDEX idx_name;
Managing triggers
Create or modify a trigger

CREATE OR MODIFY TRIGGER trigger_name
WHEN EVENT
ON table_name TRIGGER_TYPE
EXECUTE stored_procedure;

## Delete

`DELETE FROM table;` // Delete all rows
