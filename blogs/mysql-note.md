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

* **SELECT** command:

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
