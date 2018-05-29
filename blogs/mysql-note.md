# MySQL Commands

## Basic Commands

* Login via Terminal: (`root` user login)

  ```
  $ sudo mysql -u root -p
  ```

  Then enter the password.

  (Connecting to MySQL as `root` would be denied. Further configuration may apply.)

* Login via Terminal: (normal user login)

  ```
  $ mysql -u username -p
  ```

  Then enter the password.

* **SHOW** command:

  ```
  mysql> SHOW DATABASES    # Show all the databases
  mysql> SHOW TABLES       # Show all the tables (after 'using' a specific database')
  mysql> SHOW COLUMNS FROM tablename    # Show details of a table
  mysql> SHOW INDEX FROM tablename      # Show details of indexes on the table
  ```

## Command: SELECT

* `SELECT DISTINCT`: only different values are listed

* `SELECT COUNT (DISTINCT columnname) FROM tablename`: return the number of distinct values

* Limit number of returned records:

  ```
  SELECT columnname(s)
  FROM tablename
  WHERE ..condition..
  LIMIT number;
  ```

* Select smallest element:

  ```
  SELECT MIN(columnname)
  FROM tablename
  WHERE ..condition..
  ```

  ```
  SELECT MAX(columnname)
  FROM tablename
  WHERE ..condition..
  ```

* COUNT():

  ```
  SELECT COUNT(columnname)
  FROM tablename
  WHERE ..condition..
  ```

* AVG(): numeric columns only

  ```
  SELECT AVG(columnname)
  FROM tablename
  WHERE ..condition..
  ```

* SUM(): numeric columns only

  ```
  SELECT SUM(columnname)
  FROM tablename
  WHERE ..condition..
  ```

## Command: WHERE

* `SELECT columnname FROM tablename WHERE ..condition..`

* Boolean Operators: `AND`, `OR`, `NOT`

* **LIKE** Operator: ```WHERE column LIKE pattern```

  - wildcards: **%** for multiple characters and %%_%% for a single character

  - charlist wildcard: **[abc]** one of the characters

  - !charlist wildcard: **[!abc]** reverse of charlist wildcard

* **IN** operator: shorthand for multiple **OR** operators

  ```
  WHERE columnname IN (value1, value2, ...)
  ```

  ```
  WHERE columnname IN (SELECT STATEMENT)
  ```

* **WHERE** operator: `WHERE columnname BETWEEN value1 AND value2` or `WHERE column NOT BETWEEN value1 AND value2`

## Command: ORDER

* `SELECT columnname FROM tablename ORDER BY columnname (DESC)`

## Command: INSERT

* `INSERT INTO tablename (column1, column2, ...) VALUES (value1, value2, ...)`

* `INSERT INTO tablename VALUES (value1, value2, ...)`

## Command: UPDATE

* `UPDATE tablename SET column1 = value1, column2 = value2, ... WHERE ..condition..`

## Command: DELETE

* `DELETE FROM tablename WHERE ..condition..`

* `DELETE FROM tablename`: delete all rows

* `DELETE * FROM tablename`: delete all rows

## Command: JOIN

* INNER JOIN: only records that have matching values in both tables

  - Join two tables:

    ```
    SELECT Orders.OrderID, Customers.CustomerName
    FROM Orders
    INNER JOIN Customers ON Orders.CusomerID = Customers.CustomerID;
    ```

  - Join three tables:

    ```
    SELECT Orders.OrderID, Customers.CustomerName, Shippers.ShipperName
    FROM ((Orders
    INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID)
    INNER JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID);
    ```

* LEFT JOIN: all records from the left table

  ```
  SELECT Customers.CustomerName, Orders.OrderID
  FROM Customers
  LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID
  ORDER BY Customers.CustomerName;
  ```

* RIGHT JOIN: all records from the right table

* FULL OUTER JOIN: all records from both tables

* Self JOIN:

  ```
  SELECT A.CustomerName AS CustomerName1, B.CustomerName AS Customer2, A.City
  FROM Customers A, Customers B
  WHERE A.CustomerID <> B.CustomerID
  AND A.City = B.City
  ORDER BY A.City
  ```

## SQL Alias

* **AS** operator

* Example 1: alias for column(s)

  ```
  SELECT CustomerID as ID, CustomerName AS Customer FROM Customers;
  ```

  ```
  SELECT CONCAT(Address + ', ' + PostalCode + ', ' + City + ', ' + Country) AS Address FROM Customers;
  ```

  > Note: Aliases with spaces require double quotation marks or square brackets: `[Contact Person]`.

* Example 2: alias for table(s)

  ```
  SELECT o.OrderID, o.OrderDate, c.CustomerName
  FROM Customers AS c, Orders AS o
  WHERE c.CustomerName="Around the Horn", AND c.CustomerID=o.CustomerID
  ```

## Using MySQL with Python3

* Basics: (with MySQLdb)

  ```
  import MySQLdb

  db = MySQLdb.connect(host="localhost", user="username", passwd="password")
  cs = db.cursor()
  cs.execute("USE database")
  cs.execute("SHOW TABLES")    # return an integer
  tables = cs.fetchall()
  ```

## Database mysql

* Create a new user: (for non-sudo login)

  ```
  CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'passwd'
  CRANT ALL PRIVILEGES ON databasename.* to 'newuser'@'localhost'
  ```

## Else

* Testing **NULL** values: `WHERE columnname IS NULL` or `WHERE columnname IS NOT NULL`
