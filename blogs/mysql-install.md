# Install MySQL Server on Ubuntu

## Steps

1. Update package source list

   ```
   $ sudo apt update
   ```

2. Install MySQL Server

   ```
   $ sudo apt install mysql-server
   ```

3. Configure MySQL

   ```
   $ sudo mysql_secure_installation
   ```

4. Start MySQL (if not running)

   ```
   $ sudo systemctl start mysql
   ```

5. Check MySQL Status

   ```
   $ systemctl status mysql.service
   ```

6. Further Testing: ```mysqladmin```

   ```
   $ sudo mysqladmin -p -u root version
   ```

## Related Links

* How to Install MySQL on Ubuntu 18.04: https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-18-04
