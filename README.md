# Project-5-MySQL Client-Server Architecture Project  

>>**This Project involed setting up a MySQL-server and MySQL-client and configuring them to connect to each other remotely.**  

### 1.  The first step was to set up two virtual machines using AWS, one for the db-server and one for the db-client.

### 2.  Then I connected to both instances using SSH on port 22 on the security group of both instances 

### 3.  I installed mysql-server on the db-server by running the following commands;
        sudo apt update 
        sudo apt upgrade -y 
        sudo apt install mysql-server 
        
### 4.  Then i ran the security script to ensure my database is secure 
         ALTER USER 'root'@'localhost' IDENTIFIED WITH                   mysql_native_password BY 'PassWord.1';
         sudo mysql_secure_installation

### 5.  Then i logged in to the database by running 
        sudo mysql -p 

### 6.  Then i created a database user for the client using the command 
        CREATE USER 'teejay'@'%' IDENTIFIED WITH mysql_native_password BY 'Password.1';

### 7.  Next i created a databases with the command 
        CREATE DATABASE cybrox_db;
### 8.  Granting permissions to the created user 
        GRANT ALL ON cybrox_db.* TO 'teejay'@'%' WITH GRANT OPTION;
### 9.  Effecting Priviledges 
        FLUSH PRIVILEGES;
### 10. Editing Configuration files 
        sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf
### 11. Restarting mysql service so changes can be effected 
        sudo systemctl restart mysql 
### 12. Checking ip address of mysql-client 
        ip addr show 
### 13. Next i opened port 3306 in db-server security group and added   private ip of mysql-server to its inbound rules

### 14. connecting to db-server from client using the code 
        sudo mysql -u teejay -h <private ip of dbserver> -p


