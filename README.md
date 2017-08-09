## Join into 2 database
```SQL
SELECT * FROM DB1.table inner join DB2.table on DB1.table.column = DB2.table.column WHERE DB1.table.column = DB2.table.column ORDER BY `id` ASC
```
-----------------------------
## Downgrade from PHP 7 to PHP 5.6 on Ubuntu 16.04
##### 1. Re-Install PHP 5.6


```bash
sudo add-apt-repository ppa:ondrej/php
sudo apt-get update
sudo apt-get install php7.0 php5.6 php5.6-mysql php-gettext php5.6-mbstring php-mbstring php7.0-mbstring php-xdebug libapache2-mod-php5.6 libapache2-mod-php7.0
```
##### 2. Switch PHP version:

From php5.6 to php7.0:
Apache:
```bash
sudo a2dismod php5.6 ; sudo a2enmod php7.0 ; sudo service apache2 restart
```
CLI:
```bash
sudo update-alternatives --set php /usr/bin/php7.0
```

From php7.0 to php5.6:
Apache:
```bash
sudo a2dismod php7.0 ; sudo a2enmod php5.6 ; sudo service apache2 restart
```
CLI:
```bash
sudo update-alternatives --set php /usr/bin/php5.6
```
-----------------------
## Install XML-php on linux
```bash
apt-get install libxml2-utils
```
if above code is not working
```bash
sudo apt-get install php-curl php-gd php-mbstring php-mcrypt php-xml php-xmlrpc
sudo service apache2 restart
```
