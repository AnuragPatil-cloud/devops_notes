## RDS (Relational Database Service)
DBMS - database management system
SQL - structured query language

relational database = tabular formate 

-----------------------------------
Database engines (server)
1. Oracle
2. MySQL
3. PostgreSQL
4. SQL Server
5. MariaDB

EC2 server - instance --> DB engin - start - start using 

RDS - DB-instance (DB server)

Advantages of RDS
1. no need to manage DB engin 
2. highly scalabal 
3. automated backup
4. automated patching
5. automated monitoring
6. vertical auto scaling and horizontal scaling 


EC2 - instance and lanch DB engin

mariadb - mysql -- 3306 

## practical lab 
create an EC2 instance and host mariadb server 
```bash
sudo apt update -y 
sudo apt install mariadb-server -y
sudo systemctl start mariadb
sudo systemctl enable mariadb
```
check mariadb status
```bash
systemctl status mariadb
```
Q1. difference between start and enable

to run mariadb secure installation
```bash
sudo mariadb-secure-installation
```
```bash
sudo mariadb -u root -p
```

```bash
sudo apt install mariadb-client -y
``` 
```bash 
mysql --version
```
```sql
CREATE DATABASE company;
USE company;

CREATE TABLE employees (
  id INT PRIMARY KEY AUTO_INCREMENT,
  name VARCHAR(50),
  role VARCHAR(50),
  salary INT
);

INSERT INTO employees VALUES (1,'Mukund','DevOps',50000);

SELECT * FROM employees;
```

how to take backup of this database (run on hosting server)
```bash 
mysqldump -h localhost -u root -p -d studentapp > /mnt/studentapp_backup.sql
```
DELETE THE TABLE 
```bash
DROP TABLE table_name;
```

restore database from backup file
```bash
mysql -h localhost -u root -p STUDENTAPP < /mnt/studentapp_backup.sql
```
