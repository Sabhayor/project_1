# PROJECT 1 - WEB STACK IMPLEMENTATION (LAMP STACK) IN AWS
## STEP 1 — INSTALLING APACHE AND UPDATING THE FIREWALL
### Install Apache using Ubuntu’s package manager ‘apt’ 
- `sudo apt install apache2`

![Apache installation](./images/install-apache.png)
### Verify that apache2 is running as a Service in OS
- `sudo systemctl status apache2`

![Apache status](./images/apache-status.png)
### Open TCP port 80 which is the default port for web browsers to receive traffic
![TCP Port 80](./images/tcp-port-80.png)
### Test that Apache HTTP server can respond to requests from the Internet - type http://Public-IP-Address:80 in your browser

 ![Internet request](./images/internet-request.png)


 ## STEP 2 — INSTALLING MYSQL
 ### Install mysql
 - `$ sudo apt install mysql-server`

 ![Install mysql](./images/install-mysql.png)
 ### Log in to the MySQL console
- `sudo mysql`

 ![mysql console](./images/mysql-console.png)
 ### Run security script that comes pre-installed with MySQL to remove some insecure default settings
 - `ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';`

  ![mysql security](./images/mysql-security.png)
  ### Test that you’re able to log in to the MySQL console
 -  `$ sudo mysql -p`

![Console login](./images/console-login.png)


## STEP 3 — INSTALLING PHP
### Install PHP
- `sudo apt install php libapache2-mod-php php-mysql`

![Install PHP](./images/install-php.png)
### Confirm your PHP version
- `php -v`

![PHP version](./images/php-version.png)


## STEP 4 — CREATING A VIRTUAL HOST FOR YOUR WEBSITE USING APACHE
### Setup domain/Create project directory
- `sudo mkdir /var/www/projectlamp`

![Project directory](./images/project-directory.png)
###  Assign ownership to directory
- `sudo chown -R $USER:$USER /var/www/projectlamp`
### Create Virtual Host conf for project
- `sudo vim /etc/apache2/sites-available/projectlamp.conf`

![Virtual host](./images/virtual-host.png)
### Enable project
- `sudo a2ensite projectlamp`

![Enable site](./images/enable-site.png)
### Disable default site
- `sudo a2dissite 000-default`

![Disable site](./images/disable-site.png)
### Test configurations
- `sudo apache2ctl configtest`

![configuration test](./images/configuration-test.png)
### Reload Apache2 service
![Reload apache](./images/reload-apache.png)
- `sudo apache2ctl configtest`
### Reload Apache2 service
- `sudo systemctl reload apache2`
### Create an index.html file
- `sudo echo 'Hello LAMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html`

![Index page](./images/html-index.png)
![Host response](./images/host-response.png)


## STEP 5 — ENABLE PHP ON THE WEBSITE
### Edit dir.conf to place index.php at higher precedence
- `sudo vim /etc/apache2/mods-enabled/dir.conf`

![Change precedence](./images/change-precedence.png)
### Create PHP index page
- `sudo vim /var/www/projectlamp/index.php`

![PHP Index](./images/php-index.png)









