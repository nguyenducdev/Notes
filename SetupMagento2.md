SETUP ENVIRONMENT UBUNTU SERVER RUN MAGENTO 2 (LAMP)

B1: Setup a Vitrual Machine Ubuntu Server:
B2: Install APACHE 2.4
- sudo apt-get update && sudo apt-get upgrade
- sudo apt-get -y install apache2
- sudo a2enmod rewrite
- sudo service apache2 start	
B2: Install PHP7
-  sudo apt-get -y update
- sudo add-apt-repository ppa:ondrej/php
- sudo apt-get -y update
- sudo apt-get install -y php7.0 libapache2-mod-php7.0 php7.0 php7.0-common php7.0-gd php7.0-mysql php7.0-mcrypt php7.0-curl php7.0-intl php7.0-xsl php7.0-mbstring php7.0-zip php7.0-bcmath
Config file php.ini (/etc/php/7.0/apache2)
- date.timezone = Asia/Ho_Chi_Minh
- max_execution_time = 18000
- max_input_time = 6000
- memory_limit = 1024M
- post_max_size = 128M
- upload_max_filesize = 32M
B3: Install Msysql (>5.6)
- sudo apt-get -y install mysql-server mysql-client
- sudo service mysql restart


B4: Setup magento 2
- Create database
    - mysql -uroot -p
    - CREATE DATABASE magento;
    - grant all privileges on DATABASE_NAME.* to USERNAME@localhost identified by 'PASSWORD';  
    - \q
- Create domain and foder setup magento 2
    - sudo mkdir -p /var/www/mymagento.com/public_html
    - cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/mymagento.com.conf
    - sudo nano /etc/apache2/sites-available/mymagento.conf
    - edit file mymagento.com.conf
		[Code]
		<VirtualHost *:80>
			DocumentRoot /var/www/mymagento.com/public_html
			<Directory /var/www/mymagento.com/public_html>
				Options Indexes FollowSymLinks MultiViews
				AllowOverride All
			</Directory>
		</VirtualHost>
		[/Code]
    - sudo a2ensite mymagento.com.conf
    - cd /var/www/mymagento.com/public_html
    - Copy and unzip source code magento 2
    - Set 777 all file source code
    - Run


Wish success !