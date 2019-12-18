# MySQL Tutorial

###  Install MySQL
```
sudo apt-get update
sudo apt-get install mysql-server
sudo mysql_secure_installation utility
sudo systemctl start mysql
sudo systemctl enable mysql
```
### Allow remote access
```
sudo ufw enable
sudo ufw allow mysql
```
### Start the mysql shell
```
mysql -u root -p
```
### Set the root password
```
UPDATE mysql.user SET Password = PASSWORD('password') WHERE User = 'root';
```
or
```
UPDATE mysql.user SET authentication_string = PASSWORD('password') WHERE User = 'root';
```
then
```
FLUSH PRIVILEGES;
```
### Create a database
```
CREATE DATABASE demodb;
```
### Add a database user
```
INSERT INTO mysql.user (User,Host,authentication_string,ssl_cipher,x509_issuer,x509_subject) VALUES('demouser','localhost',PASSWORD('demopassword'),'','','');
FLUSH PRIVILEGES;
```
### Grant database user permissions
```
GRANT ALL PRIVILEGES ON demodb.* to demouser@localhost;
FLUSH PRIVILEGES;
SHOW GRANTS FOR 'demouser'@'localhost';
```
### Import from *.sql
```
mysql -u <username> -p <databasename> < <filename.sql>
```
or in mysql shell
```
source <filepath/filename.sql>
```