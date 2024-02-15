# php-latest-project

# Steps for installing LAMP on Amazon Linux 2023

# Update Amazon Linux 2023
1. yum update -y

# Install LAMP packages
3. yum install -y httpd wget php-fpm php-mysqli php-json php php-devel mariadb105-server

# Verify the installed versions
4. httpd -v
5. php -v
6. mysql --version

# Start the httpd service
7. systemctl start httpd
8. systemctl enable httpd

# Verify if the PHP installed properly
9. echo "<?php phpinfo(); ?>" > /var/www/html/phpinfo.php
10. Access the application using EC2 public IP like this (http://3.84.215.159/phpinfo.php) (Replace the IP with your EC2 public ip)

# Secure the database server
11. systemctl start mariadb
12. systemctl enable mariadb
13. mysql_secure_installation
14. By default, the root account does not have a password. Press Enter
15. Type Y to set a password, and type a secure password twice
16. Then type Y on every prompt till end of the process

# Login to the database and create a database as "registration"
17. mysql -u root -p
18. create database registration;
19. then copy the mysql script from "dbscript.sql" to create the table

# Download the application code from Github to the html folder, unzip and copy the all the files to html folder
20. cd /var/www/html
21. wget https://github.com/sudhirr4u/php-latest-project/archive/refs/heads/main.zip
22. unzip main.zip
23. rm -rf main.zip
24. cp -r php-latest-project-main/* .
25. rm -rf php-latest-project-main/

# Restart the MariaDb and Httpd service
26. systemctl restart mariadb
27. systemctl restart httpd

# Access the simple web application by the EC2 public ip
28. http://3.84.215.159 (Replace the IP with your EC2 public ip)
29. For first time register an user by entering the details
30. Then try to login using registered user id and password
