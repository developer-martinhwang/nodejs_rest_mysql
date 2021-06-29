## Installing MySQL to Fedora 34 
## Adding the MySQL repository to Fedora
sudo dnf install https://repo.mysql.com//mysql80-community-release-fc31-1.noarch.rpm 

## Installing MySQL on Fedora
sudo dnf install mysql-community-server 

## Start MySQL Service and Enable at Loggin:
sudo systemctl start mysqld 
sudo systemctl enable mysqld 
## find Default Password, For security reasons, MySQL generates a temporary root key. Please note that MySQL has even stricter security policies than MariaDB.
sudo grep 'temporary password' /var/log/mysqld.log

## Configuring MySQL before the first use
sudo mysql_secure_installation

## Local MySQL PW:
Martin123456!

Then, answer the security questions as you prefer. or just say yes to all of them.

## Using MYSQL
sudo mysql -u root -p

## Removing MySQL
I suggest to remove in the following way, the most appropriate and safe way without removing many dependencies is:
sudo rpm -e --nodeps mysql-community-libs mysql-community-common mysql-community-server

## Using MYSQL
sudo mysql -u root -p

## Creating DB and showinng DB
CREATE DATABASE testdb;
show databases;
## Using DB
USE testdb;
## Creating table
CREATE TABLE IF NOT EXISTS `customers` (
  id int(11) NOT NULL PRIMARY KEY AUTO_INCREMENT,
  email varchar(255) NOT NULL,
  name varchar(255) NOT NULL,
  active BOOLEAN DEFAULT false
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
show tables;

## Now we can check which database is selected with the help of DATABASE() from dual. The query is as follows 
## Check current DB
SELECT DATABASE() FROM DUAL;
status;

## You can find more details about mysql module at: https://www.npmjs.com/package/mysql.

## “Error: ER_NOT_SUPPORTED_AUTH_MODE: Client does not support authentication protocol requested by server; consider upgrading MySQL client” Code Answer’s
mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'your_new_password';
mysql> FLUSH PRIVILEGES;
mysql> quit


