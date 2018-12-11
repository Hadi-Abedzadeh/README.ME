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
apt install php libapache2-mod-php

php-ini

```
extension=apcu.so
extension=apcu.so
apc.enabled=1
apc.shm_size=1024M
```

### Htaccess not working ...
after installation apache
```bash
sudo a2enmod rewrite
service apache2 restart
sudo nano /etc/apache2/sites-available/000-default.conf
```
```bash
VirtualHost *:80>
    <Directory /var/www/html>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Require all granted
    </Directory>

    . . .
</VirtualHost>
```
```bash
sudo nano /var/www/html/.htaccess
```
put command into htaccess
```bash
RewriteEngine on
```

more description

https://www.digitalocean.com/community/tutorials/how-to-rewrite-urls-with-mod_rewrite-for-apache-on-ubuntu-16-04

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

## Remove mysql from ubuntu
```bash
sudo apt-get remove dbconfig-mysql
sudo apt-get remove --purge mysql*
sudo apt-get autoremove
sudo apt-get autoclean
```
and for install
```bash
sudo apt-get install mysql-server
```

## mysql remote query
```bash
/etc/mysql/mysql.conf.d/mysqld.cnf
bind-address		= 0.0.0.0
```
and from phpmyadmin change privilage user access and can run command (SELECT ALL CHECKBOX - SELECT, INSERT, UPDATE ...)

### Remove completely Android studio
To Completely Remove Android Studio from Windows:

Step 1: Run the Android Studio uninstaller

The first step is to run the uninstaller. Open the Control Panel and under Programs, select Uninstall a Program. After that, click on "Android Studio" and press Uninstall. If you have multiple versions, uninstall them as well.

Step 2: Remove the Android Studio files

To delete any remains of Android Studio setting files, in File Explorer, go to your user folder (%USERPROFILE%), and delete .android, .AndroidStudio and any analogous directories with versions on the end, i.e. .AndroidStudio1.2, as well as .gradle and .m2 if they exist.

Then go to %APPDATA% and delete the JetBrains directory.

Finally, go to C:\Program Files and delete the Android directory.

Step 3: Remove SDK

To delete any remains of the SDK, go to %LOCALAPPDATA% and delete the Android directory.

Step 4: Delete Android Studio projects

Android Studio creates projects in a folder %USERPROFILE%\AndroidStudioProjects, which you may want to delete.

https://stackoverflow.com/questions/39953495/how-to-completely-uninstall-android-studio-from-windowsv10

## Remove .php extention
Gumbo's answer in the Stack Overflow question How to hide the .html extension with Apache mod_rewrite should work fine.

Re 1) Change the .html to .php

Re a.) Yup, that's possible, just add #tab to the URL.

Re b.) That's possible using QSA (Query String Append), see below.

This should also work in a sub-directory path:

RewriteCond %{REQUEST_FILENAME}.php -f
RewriteRule !.*\.php$ %{REQUEST_FILENAME}.php [QSA,L]

https://stackoverflow.com/questions/4026021/remove-php-extension-with-htaccess

### SQL COUNT OUTPUT ROWS
```sql
SET @var:=0;
SELECT *,(@var:=@var+1) AS `rank` FROM `table`;
```

### INSTALL PHP7 Completely

```bash
 sudo rm /var/cache/apt/archives/lock
 sudo rm /var/lib/dpkg/lock
 rm /var/lib/dpkg/lock
 apt-get install update
 sudo rm /var/lib/dpkg/lock
 sudo dpkg --configure -a
 dpkg --configure -a
 apt-get install update
 apt-get install apache2
   
   
 aptitude search php5-
 apt-get install php-mbstring php7.0-mbstring php-xdebug
 apt-get install libapache2-mod-php7.0
 apt-get install php-intl
 apt-get install php-devel php-mysqlnd gcc libtool
 apt-get install php-devel
 sudo apt-get install php-devel
 sudo apt-get install php-mcrypt php-curl php-gd
 sudo apt-get install php7.0
 sudo a2enmod rewrite
 service apache2 restart

 apt-get install mcrypt
 sudo php5enmod mcrypt
 apt-get install zip
 sudo apt-get install php libapache2-mod-php
 sudo a2enmod php7.0

 apt-get install phpenmod
 apt-get install php7enmod
 apt-get install php5enmod
```
### PHP Base-AUTH : basic authentication

After cheking FPM function in the server (WHM)
create .htaccess file and write into:
```bash
RewriteEngine on
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{REQUEST_URI} !\.(jpg|png|css|js|less|txt|ttf|woff|woff2|xml)$
RewriteRule ^(.*)$ ./index.php/$1 [L]

Order Allow,Deny
Allow from all

SetEnvIf Authorization .+ HTTP_AUTHORIZATION=$0
Options +FollowSymLinks
```

### Disable GUI mode in tinker board || linux
```bash
Text mode login:
systemctl set-default multi-user.target

Back to full desktop: 
systemctl set-default graphical.target
```
https://tinkerboarding.co.uk/forum/thread-665.html


### Wordpress renew database tables
```bash
UPDATE wp_options SET option_value = replace(option_value, 'http://www.oldurl', 'http://www.newurl') WHERE option_name = 'home' OR option_name = 'siteurl';

UPDATE wp_posts SET guid = replace(guid, 'http://www.oldurl','http://www.newurl');

UPDATE wp_posts SET post_content = replace(post_content, 'http://www.oldurl', 'http://www.newurl');

UPDATE wp_postmeta SET meta_value = replace(meta_value,'http://www.oldurl','http://www.newurl');```

### Up internet speed in linux ubuntu
I had a similar issue with my system preferring IPv6 over IPv4. To change to preferring IPv4 over IPv6.

Open a terminal

```
sudo nano /etc/gai.conf
```
Locate #precedence ::ffff:0:0/96 100 and and remove the #.
You may have to reboot. Should notice the difference quickly

