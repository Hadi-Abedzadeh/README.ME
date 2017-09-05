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
--------------------
# Apache
### setup apache to php
php-ini

```
extension=apcu.so
extension=apcu.so
apc.enabled=1
apc.shm_size=1024M
```
### DDoS Protection
```bash
wget http://www.inetbase.com/scripts/ddos/install.sh
sh install.sh
cd /usr/local/ddos/;./ddos.sh
sh /usr/local/ddos/ddos.sh
nano /usr/local/ddos/ddos.conf
```

### Add usergroup
```bash
groupadd http-web
useradd -d /var/www/ -g http-web -s /bin/nologin http-web
nano /etc/apache2/conf/httpd.conf
User http-web
Group http-web
service httpd restart
```

### Symlink
```bash
nano /etc/apache2/conf/httpd.conf
Options -FollowSymLinks
Options -Includes
Options -ExecCGI
service httpd restart
```
### Permission on directory apache
```bash
chown -R root:root /usr/local/apache
chmod -R o-rwx /usr/local/apache
```

### php-ini
```bash
disable_functions = show_source, system, shell_exec, passthru, exec, phpinfo, proc_terminate, proc_open, symlink, proc_close, popen, dl, escapeshellarg, escapeshellcmd
```
## SQL error on "GROUP BY" query:
```sql
SET GLOBAL sql_mode=(SELECT REPLACE(@@sql_mode,'ONLY_FULL_GROUP_BY',''));
```


## For loop and append output to text file
```bash
for /l %x in (1, 1, 200) do echo %x >> output.txt
```
