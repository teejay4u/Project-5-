# Project-5-MySQL Client-Server Architecture Project  

>>**This Project involed setting up a MySQL-server and MySQL-client and configuring them to connect to each other remotely.**  

### 1.  The first step was to set up two virtual machines using AWS, one for the db-server and one for the db-client.

### 2.  Then I connected to both instances using SSH on port 22 on the security group of both instances 
        ssh -i "privatekey.pem" ubuntu@ec2<pub-ip>.compute-1.amazonaws.com

### 3.  I installed mysql-server on the db-server by running the following commands;
        # For Server
        sudo apt update 
        sudo apt upgrade -y
        sudo apt install mysql-server 

        # For Client
        sudo apt update 
        sudo apt upgrade -y
        sudo apt install mysql-client

### 4. To show if service is running 
        Sudo systemctl status mysql
        
### 5.  Then i ran the security script to ensure my database is secure 
         ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'Password.1';

         sudo mysql_secure_installation

### 6.  Then i logged in to the database by running 
        sudo mysql -p 

### 7.  Then i created a database user for the client using the command 
        CREATE USER 'username'@'%' IDENTIFIED WITH mysql_native_password BY 'Password.1';

### 8.  Next i created a databases with the command 
        CREATE DATABASE cybrox_db;
### 9.  Granting permissions to the created user 
        GRANT ALL ON cybrox_db.* TO '<username>'@'%' WITH GRANT OPTION;
### 10.  Effecting Priviledges 
        FLUSH PRIVILEGES;
### 11. Editing Configuration files 
        sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf
### 12. Restarting mysql service so changes can be effected 
        sudo systemctl restart mysql 
### 13. Checking ip address of mysql-client 
        ip addr show 
### 14. Next i opened port 3306 in db-server security group and added   private ip of mysql-server to its inbound rules

### 15. connecting to db-server from client using the code 
        sudo mysql -u teejay -h <private ip of dbserver> -p

### 16. Creating the Virtual Machines on AWS Console
        
![](Instances%20Running.png)

### 17. mysql service running on server

![](Mysql%20service%20running.png)

### 18. Securing DB-server 

![](Securing%20Mysql%20Database.png)

### 19. Creating Db-user on server 

![](Creating%20Db%20user%20on%20server.png)

### 20. Granting Permissions to DB-user 

![](Granting%20permissions%20to%20Db-user.png)

### 21. Setting Bind address to accept all ip address from client user

![](SETTING%20BIND%20ADDRESS%20TO%20ALLOW%20ANYWHERE.png)

### 22. Connected to DB-server from mysql-Client

![](Connected%20to%20Db-server%20from%20client%20server.png)

### 23. Showing available databases on db-server from mysql-client

![](showing%20database%20available%20from%20client%20server.png)