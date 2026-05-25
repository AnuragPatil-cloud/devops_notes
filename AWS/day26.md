## RDS database 
- amazon manage database service
- relational database service
- supports multiple database engines like MySQL, PostgreSQL, Oracle, SQL Server, and MariaDB
- provides high availability, scalability, and security
- automated backups, snapshots, and replication


## read replica 
- a read-only copy of the primary database
- used to offload read traffic from the primary database
- can be in the same region or in a different region
- can be promoted to a standalone database instance
<img width="433" height="269" alt="Screenshot 2026-01-06 at 4 44 11 PM" src="https://github.com/user-attachments/assets/1ec53b34-bb9c-4100-b1a2-663b1c54a413" />


## Multi-AZ deployments
- provides high availability and failover support
- automatically replicates data to a standby instance in a different availability zone
- in case of a failure, the standby instance is automatically promoted to primary
- minimizes downtime and data loss
<img width="725" height="483" alt="Screenshot 2026-01-06 at 4 50 25 PM" src="https://github.com/user-attachments/assets/b7141e51-7673-4f90-b233-2e52b8ace05e" />

```
what is Read Replica ?
What is Multi-AZ Deployment ?
diff between Read Replica vs Multi-AZ deployment ? 
```
---
## project on RDS database [EasyCRUD](https://github.com/mukundDeo9325/EasyCRUD.git)
## frontend
```bash
    1  apt update -y
    2  git clone https://github.com/mukundDeo9325/EasyCRUD.git
    3  ls
    4  cd e
    5  cd EasyCRUD/
    6  ls
    7  cd frontend/
    8  ls
    9  apt update && apt install nodejs npm -y
   10  vim .env 
   11  npm install
   12  npm run build 
   13  ls 
   14  apt install apache2 -y
   15  systemctl start apache2
   16  cp -rf dist/* /var/www/html/
   17  history 
   ```

## backend
```bash
1  ls
    2  apt update -y 
    3  git clone https://github.com/mukundDeo9325/EasyCRUD.git
    4  ls
    5  cd EasyCRUD/
    6  ls
    7  cd backend/
    8  ls
    9  cd src/main/resources/
   10  ls
   11  vim application.properties 
   12  cd ../../..
   13  ls
   14  java -version
   15  apt update && apt install openjdk-17-jdk -y
   16  java -version
   17  apt install maven -y
   18  mvn -version
   19  mvn clean package
   20  ls target/
   21  java -jar target/student-registration-backend-0.0.1-SNAPSHOT.jar 
   22  history 
   ```  
   
