
You said:
Debian 9 lamp  full tutorial
ChatGPT said:
Debian 9 Lamp Stack Full Tutorial

Debian 9 (Stretch) – Full LAMP Stack Installation Tutorial
LAMP = Linux + Apache + MySQL/MariaDB + PHP
This guide walks you through installing and configuring a complete LAMP stack on Debian 9 (Stretch).

1. Prerequisites
Debian 9 installed (minimal or standard)

Root access or a user with sudo

Internet connection

Check your Debian version:

cat /etc/debian_version
2. Update the System
Always start by updating package lists and installed packages:

sudo apt update
sudo apt upgrade -y
(Optional but recommended):

sudo apt install -y apt-transport-https ca-certificates curl
3. Install Apache Web Server
3.1 Install Apache
sudo apt install -y apache2
3.2 Start and Enable Apache
sudo systemctl start apache2
sudo systemctl enable apache2
3.3 Verify Apache
Open a browser and visit:

http://your_server_ip/
You should see the Apache2 Debian Default Page.

3.4 Apache Service Commands
sudo systemctl status apache2
sudo systemctl restart apache2
sudo systemctl stop apache2
4. Install MariaDB (MySQL Alternative)
Debian 9 uses MariaDB by default (fully compatible with MySQL).

4.1 Install MariaDB
sudo apt install -y mariadb-server mariadb-client
4.2 Start and Enable MariaDB
sudo systemctl start mariadb
sudo systemctl enable mariadb
4.3 Secure MariaDB
sudo mysql_secure_installation
Recommended answers:

Set root password: Yes

Remove anonymous users: Yes

Disallow remote root login: Yes

Remove test database: Yes

Reload privilege tables: Yes

4.4 Test Login
mysql -u root -p
Exit:

EXIT;
5. Install PHP
Debian 9 ships with PHP 7.0.

5.1 Install PHP and Common Modules
sudo apt install -y php php-mysql php-cli php-curl php-gd php-mbstring php-xml php-zip libapache2-mod-php
5.2 Verify PHP Version
php -v
6. Configure Apache for PHP
6.1 Ensure PHP Module Is Enabled
sudo a2enmod php7.0
sudo systemctl restart apache2
6.2 Change Directory Index Priority (Optional)
Edit:

sudo nano /etc/apache2/mods-enabled/dir.conf
Change:

DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
To:

DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
Restart Apache:

sudo systemctl restart apache2
7. Test PHP Processing
Create a PHP info file:

sudo nano /var/www/html/info.php
Add:

<?php
phpinfo();
?>
Open in browser:

http://your_server_ip/info.php
If PHP info page appears, PHP is working.

Important: Remove this file after testing

sudo rm /var/www/html/info.php
8. Create a Virtual Host (Optional but Recommended)
8.1 Create Website Directory
sudo mkdir -p /var/www/example.com/public_html
sudo chown -R www-data:www-data /var/www/example.com
sudo chmod -R 755 /var/www/example.com
8.2 Create Virtual Host File
sudo nano /etc/apache2/sites-available/example.com.conf
Add:

<VirtualHost *:80>
    ServerName example.com
    ServerAlias www.example.com
    DocumentRoot /var/www/example.com/public_html

    <Directory /var/www/example.com/public_html>
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/example.com_error.log
    CustomLog ${APACHE_LOG_DIR}/example.com_access.log combined
</VirtualHost>
8.3 Enable Virtual Host
sudo a2ensite example.com.conf
sudo a2dissite 000-default.conf
sudo systemctl reload apache2
9. Test PHP in Virtual Host
sudo nano /var/www/example.com/public_html/index.php
Add:

<?php echo "LAMP Stack is working!"; ?>
Visit:

http://example.com
10. Firewall Configuration (Optional)
If UFW is installed:

sudo apt install -y ufw
sudo ufw allow OpenSSH
sudo ufw allow 'Apache Full'
sudo ufw enable
Check status:

sudo ufw status
11. Useful Paths
Web root: /var/www/html

Apache config: /etc/apache2/

Virtual hosts: /etc/apache2/sites-available/

PHP config: /etc/php/7.0/apache2/php.ini

MariaDB data: /var/lib/mysql

12. Final Check
apache2 -v
php -v
mysql --version
Your Debian 9 LAMP stack is now fully installed and configured 🎉

If you want, I can also provide:

🔒 LAMP security hardening

🚀 PHP performance tuning

📦 phpMyAdmin installation

🌐 HTTPS with Let’s Encrypt

I’ve created a complete, step-by-step Debian 9 (Stretch) LAMP stack tutorial in the canvas for you.

It covers:

System update

Apache installation & configuration

MariaDB (MySQL) setup and security

PHP 7.0 installation

Apache–PHP integration

Virtual hosts

Firewall basics

Testing & verification

If you want, I can extend it further with:

phpMyAdmin setup

Let’s Encrypt SSL (HTTPS)

LAMP security hardening

PHP & Apache performance tuning

Running multiple sites on one server

Just tell me 👍

You said:
Make it in full md
ChatGPT said:
Done ✅
I’ve converted the tutorial into a pure, complete Markdown (.md) file.

👉 Download the full Markdown file

You can now:

Open it in any Markdown editor

Push it to GitHub/GitLab

Convert it to PDF/HTML

Use it as documentation or a blog post

If you want, I can also:

Split it into chapters (README-style)

Add code-block language hints for static site generators

Create an Ansible / bash automation version

Convert it to PDF or HTML

Just tell me what you need next. 

You said:
Make it all txt only copy by my self
ChatGPT said:
Below is the FULL TUTORIAL IN PLAIN TEXT ONLY
(no Markdown, no formatting tricks — you can copy-paste it anywhere)

Debian 9 (Stretch) – Full LAMP Stack Installation Tutorial

LAMP = Linux + Apache + MySQL/MariaDB + PHP

This guide explains how to install and configure a complete LAMP stack on Debian 9 (Stretch).

Prerequisites

Debian 9 installed

Root access or sudo user

Internet connection

Check Debian version:

cat /etc/debian_version

Update the System

sudo apt update
sudo apt upgrade -y

Optional but recommended:

sudo apt install -y apt-transport-https ca-certificates curl

Install Apache Web Server

Install Apache:

sudo apt install -y apache2

Start and enable Apache:

sudo systemctl start apache2
sudo systemctl enable apache2

Test Apache:

Open a browser and visit:
http://your_server_ip/

You should see the Apache default page.

Useful Apache commands:

sudo systemctl status apache2
sudo systemctl restart apache2
sudo systemctl stop apache2

Install MariaDB (MySQL)

Install MariaDB server and client:

sudo apt install -y mariadb-server mariadb-client

Start and enable MariaDB:

sudo systemctl start mariadb
sudo systemctl enable mariadb

Secure MariaDB:

sudo mysql_secure_installation

Recommended answers:

Set root password: Yes

Remove anonymous users: Yes

Disallow remote root login: Yes

Remove test database: Yes

Reload privilege tables: Yes

Test database login:

mysql -u root -p

Exit MariaDB:

EXIT;



You said:
Debian 9 lamp  full tutorial
ChatGPT said:
Debian 9 Lamp Stack Full Tutorial

Debian 9 (Stretch) – Full LAMP Stack Installation Tutorial
LAMP = Linux + Apache + MySQL/MariaDB + PHP
This guide walks you through installing and configuring a complete LAMP stack on Debian 9 (Stretch).

1. Prerequisites
Debian 9 installed (minimal or standard)

Root access or a user with sudo

Internet connection

Check your Debian version:

cat /etc/debian_version
2. Update the System
Always start by updating package lists and installed packages:

sudo apt update
sudo apt upgrade -y
(Optional but recommended):

sudo apt install -y apt-transport-https ca-certificates curl
3. Install Apache Web Server
3.1 Install Apache
sudo apt install -y apache2
3.2 Start and Enable Apache
sudo systemctl start apache2
sudo systemctl enable apache2
3.3 Verify Apache
Open a browser and visit:

http://your_server_ip/
You should see the Apache2 Debian Default Page.

3.4 Apache Service Commands
sudo systemctl status apache2
sudo systemctl restart apache2
sudo systemctl stop apache2
4. Install MariaDB (MySQL Alternative)
Debian 9 uses MariaDB by default (fully compatible with MySQL).

4.1 Install MariaDB
sudo apt install -y mariadb-server mariadb-client
4.2 Start and Enable MariaDB
sudo systemctl start mariadb
sudo systemctl enable mariadb
4.3 Secure MariaDB
sudo mysql_secure_installation
Recommended answers:

Set root password: Yes

Remove anonymous users: Yes

Disallow remote root login: Yes

Remove test database: Yes

Reload privilege tables: Yes

4.4 Test Login
mysql -u root -p
Exit:

EXIT;
5. Install PHP
Debian 9 ships with PHP 7.0.

5.1 Install PHP and Common Modules
sudo apt install -y php php-mysql php-cli php-curl php-gd php-mbstring php-xml php-zip libapache2-mod-php
5.2 Verify PHP Version
php -v
6. Configure Apache for PHP
6.1 Ensure PHP Module Is Enabled
sudo a2enmod php7.0
sudo systemctl restart apache2
6.2 Change Directory Index Priority (Optional)
Edit:

sudo nano /etc/apache2/mods-enabled/dir.conf
Change:

DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
To:

DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
Restart Apache:

sudo systemctl restart apache2
7. Test PHP Processing
Create a PHP info file:

sudo nano /var/www/html/info.php
Add:

<?php
phpinfo();
?>
Open in browser:

http://your_server_ip/info.php
If PHP info page appears, PHP is working.

Important: Remove this file after testing

sudo rm /var/www/html/info.php
8. Create a Virtual Host (Optional but Recommended)
8.1 Create Website Directory
sudo mkdir -p /var/www/example.com/public_html
sudo chown -R www-data:www-data /var/www/example.com
sudo chmod -R 755 /var/www/example.com
8.2 Create Virtual Host File
sudo nano /etc/apache2/sites-available/example.com.conf
Add:

<VirtualHost *:80>
    ServerName example.com
    ServerAlias www.example.com
    DocumentRoot /var/www/example.com/public_html

    <Directory /var/www/example.com/public_html>
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/example.com_error.log
    CustomLog ${APACHE_LOG_DIR}/example.com_access.log combined
</VirtualHost>
8.3 Enable Virtual Host
sudo a2ensite example.com.conf
sudo a2dissite 000-default.conf
sudo systemctl reload apache2
9. Test PHP in Virtual Host
sudo nano /var/www/example.com/public_html/index.php
Add:

<?php echo "LAMP Stack is working!"; ?>
Visit:

http://example.com
10. Firewall Configuration (Optional)
If UFW is installed:

sudo apt install -y ufw
sudo ufw allow OpenSSH
sudo ufw allow 'Apache Full'
sudo ufw enable
Check status:

sudo ufw status
11. Useful Paths
Web root: /var/www/html

Apache config: /etc/apache2/

Virtual hosts: /etc/apache2/sites-available/

PHP config: /etc/php/7.0/apache2/php.ini

MariaDB data: /var/lib/mysql

12. Final Check
apache2 -v
php -v
mysql --version
Your Debian 9 LAMP stack is now fully installed and configured 🎉

If you want, I can also provide:

🔒 LAMP security hardening

🚀 PHP performance tuning

📦 phpMyAdmin installation

🌐 HTTPS with Let’s Encrypt

I’ve created a complete, step-by-step Debian 9 (Stretch) LAMP stack tutorial in the canvas for you.

It covers:

System update

Apache installation & configuration

MariaDB (MySQL) setup and security

PHP 7.0 installation

Apache–PHP integration

Virtual hosts

Firewall basics

Testing & verification

If you want, I can extend it further with:

phpMyAdmin setup

Let’s Encrypt SSL (HTTPS)

LAMP security hardening

PHP & Apache performance tuning

Running multiple sites on one server

Just tell me 👍

You said:
Make it in full md
ChatGPT said:
Done ✅
I’ve converted the tutorial into a pure, complete Markdown (.md) file.

👉 Download the full Markdown file

You can now:

Open it in any Markdown editor

Push it to GitHub/GitLab

Convert it to PDF/HTML

Use it as documentation or a blog post

If you want, I can also:

Split it into chapters (README-style)

Add code-block language hints for static site generators

Create an Ansible / bash automation version

Convert it to PDF or HTML

Just tell me what you need next. 

You said:
Make it all txt only copy by my self
ChatGPT said:
Below is the FULL TUTORIAL IN PLAIN TEXT ONLY
(no Markdown, no formatting tricks — you can copy-paste it anywhere)

Debian 9 (Stretch) – Full LAMP Stack Installation Tutorial

LAMP = Linux + Apache + MySQL/MariaDB + PHP

This guide explains how to install and configure a complete LAMP stack on Debian 9 (Stretch).

Prerequisites

Debian 9 installed

Root access or sudo user

Internet connection

Check Debian version:

cat /etc/debian_version

Update the System

sudo apt update
sudo apt upgrade -y

Optional but recommended:

sudo apt install -y apt-transport-https ca-certificates curl

Install Apache Web Server

Install Apache:

sudo apt install -y apache2

Start and enable Apache:

sudo systemctl start apache2
sudo systemctl enable apache2

Test Apache:

Open a browser and visit:
http://your_server_ip/

You should see the Apache default page.

Useful Apache commands:

sudo systemctl status apache2
sudo systemctl restart apache2
sudo systemctl stop apache2

Install MariaDB (MySQL)

Install MariaDB server and client:

sudo apt install -y mariadb-server mariadb-client

Start and enable MariaDB:

sudo systemctl start mariadb
sudo systemctl enable mariadb

Secure MariaDB:

sudo mysql_secure_installation

Recommended answers:

Set root password: Yes

Remove anonymous users: Yes

Disallow remote root login: Yes

Remove test database: Yes

Reload privilege tables: Yes

Test database login:

mysql -u root -p

Exit MariaDB:

EXIT;

Install PHP 7.0

Install PHP and common extensions:

sudo apt install -y php php-mysql php-cli php-curl php-gd php-mbstring php-xml php-zip libapache2-mod-php

Verify PHP installation:

php -v

Configure Apache for PHP

Enable PHP module:

sudo a2enmod php7.0
sudo systemctl restart apache2

Edit directory index priority:

sudo nano /etc/apache2/mods-enabled/dir.conf

Change the line to:

DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm

Restart Apache:

sudo systemctl restart apache2

Test PHP

Create PHP test file:

sudo nano /var/www/html/info.php

Add this content:

<?php phpinfo(); ?>
Open in browser:

http://your_server_ip/info.php

If PHP info page appears, PHP is working.

IMPORTANT: Remove the file after testing:

sudo rm /var/www/html/info.php

Create Apache Virtual Host

Create website directory:

sudo mkdir -p /var/www/example.com/public_html
sudo chown -R www-data:www-data /var/www/example.com
sudo chmod -R 755 /var/www/example.com

Create virtual host config:

sudo nano /etc/apache2/sites-available/example.com.conf

Paste this configuration:

<VirtualHost *:80>
ServerName example.com
ServerAlias www.example.com
DocumentRoot /var/www/example.com/public_html

<Directory /var/www/example.com/public_html>
    AllowOverride All
    Require all granted
</Directory>

ErrorLog ${APACHE_LOG_DIR}/example.com_error.log
CustomLog ${APACHE_LOG_DIR}/example.com_access.log combined
</VirtualHost>
Enable virtual host and disable default site:

sudo a2ensite example.com.conf
sudo a2dissite 000-default.conf
sudo systemctl reload apache2

Test PHP in Virtual Host

Create test PHP file:

sudo nano /var/www/example.com/public_html/index.php

Add:

<?php echo "LAMP Stack is working!"; ?>
Visit in browser:

http://example.com

Firewall Configuration (Optional)

Install UFW:

sudo apt install -y ufw

Allow SSH and Apache:

sudo ufw allow OpenSSH
sudo ufw allow Apache Full

Enable firewall:

sudo ufw enable

Check firewall status:

sudo ufw status



You said:
Debian 9 lamp  full tutorial
ChatGPT said:
Debian 9 Lamp Stack Full Tutorial

Debian 9 (Stretch) – Full LAMP Stack Installation Tutorial
LAMP = Linux + Apache + MySQL/MariaDB + PHP
This guide walks you through installing and configuring a complete LAMP stack on Debian 9 (Stretch).

1. Prerequisites
Debian 9 installed (minimal or standard)

Root access or a user with sudo

Internet connection

Check your Debian version:

cat /etc/debian_version
2. Update the System
Always start by updating package lists and installed packages:

sudo apt update
sudo apt upgrade -y
(Optional but recommended):

sudo apt install -y apt-transport-https ca-certificates curl
3. Install Apache Web Server
3.1 Install Apache
sudo apt install -y apache2
3.2 Start and Enable Apache
sudo systemctl start apache2
sudo systemctl enable apache2
3.3 Verify Apache
Open a browser and visit:

http://your_server_ip/
You should see the Apache2 Debian Default Page.

3.4 Apache Service Commands
sudo systemctl status apache2
sudo systemctl restart apache2
sudo systemctl stop apache2
4. Install MariaDB (MySQL Alternative)
Debian 9 uses MariaDB by default (fully compatible with MySQL).

4.1 Install MariaDB
sudo apt install -y mariadb-server mariadb-client
4.2 Start and Enable MariaDB
sudo systemctl start mariadb
sudo systemctl enable mariadb
4.3 Secure MariaDB
sudo mysql_secure_installation
Recommended answers:

Set root password: Yes

Remove anonymous users: Yes

Disallow remote root login: Yes

Remove test database: Yes

Reload privilege tables: Yes

4.4 Test Login
mysql -u root -p
Exit:

EXIT;
5. Install PHP
Debian 9 ships with PHP 7.0.

5.1 Install PHP and Common Modules
sudo apt install -y php php-mysql php-cli php-curl php-gd php-mbstring php-xml php-zip libapache2-mod-php
5.2 Verify PHP Version
php -v
6. Configure Apache for PHP
6.1 Ensure PHP Module Is Enabled
sudo a2enmod php7.0
sudo systemctl restart apache2
6.2 Change Directory Index Priority (Optional)
Edit:

sudo nano /etc/apache2/mods-enabled/dir.conf
Change:

DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
To:

DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
Restart Apache:

sudo systemctl restart apache2
7. Test PHP Processing
Create a PHP info file:

sudo nano /var/www/html/info.php
Add:

<?php
phpinfo();
?>
Open in browser:

http://your_server_ip/info.php
If PHP info page appears, PHP is working.

Important: Remove this file after testing

sudo rm /var/www/html/info.php
8. Create a Virtual Host (Optional but Recommended)
8.1 Create Website Directory
sudo mkdir -p /var/www/example.com/public_html
sudo chown -R www-data:www-data /var/www/example.com
sudo chmod -R 755 /var/www/example.com
8.2 Create Virtual Host File
sudo nano /etc/apache2/sites-available/example.com.conf
Add:

<VirtualHost *:80>
    ServerName example.com
    ServerAlias www.example.com
    DocumentRoot /var/www/example.com/public_html

    <Directory /var/www/example.com/public_html>
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/example.com_error.log
    CustomLog ${APACHE_LOG_DIR}/example.com_access.log combined
</VirtualHost>
8.3 Enable Virtual Host
sudo a2ensite example.com.conf
sudo a2dissite 000-default.conf
sudo systemctl reload apache2
9. Test PHP in Virtual Host
sudo nano /var/www/example.com/public_html/index.php
Add:

<?php echo "LAMP Stack is working!"; ?>
Visit:

http://example.com
10. Firewall Configuration (Optional)
If UFW is installed:

sudo apt install -y ufw
sudo ufw allow OpenSSH
sudo ufw allow 'Apache Full'
sudo ufw enable
Check status:

sudo ufw status
11. Useful Paths
Web root: /var/www/html

Apache config: /etc/apache2/

Virtual hosts: /etc/apache2/sites-available/

PHP config: /etc/php/7.0/apache2/php.ini

MariaDB data: /var/lib/mysql

12. Final Check
apache2 -v
php -v
mysql --version
Your Debian 9 LAMP stack is now fully installed and configured 🎉

If you want, I can also provide:

🔒 LAMP security hardening

🚀 PHP performance tuning

📦 phpMyAdmin installation

🌐 HTTPS with Let’s Encrypt

I’ve created a complete, step-by-step Debian 9 (Stretch) LAMP stack tutorial in the canvas for you.

It covers:

System update

Apache installation & configuration

MariaDB (MySQL) setup and security

PHP 7.0 installation

Apache–PHP integration

Virtual hosts

Firewall basics

Testing & verification

If you want, I can extend it further with:

phpMyAdmin setup

Let’s Encrypt SSL (HTTPS)

LAMP security hardening

PHP & Apache performance tuning

Running multiple sites on one server

Just tell me 👍

You said:
Make it in full md
ChatGPT said:
Done ✅
I’ve converted the tutorial into a pure, complete Markdown (.md) file.

👉 Download the full Markdown file

You can now:

Open it in any Markdown editor

Push it to GitHub/GitLab

Convert it to PDF/HTML

Use it as documentation or a blog post

If you want, I can also:

Split it into chapters (README-style)

Add code-block language hints for static site generators

Create an Ansible / bash automation version

Convert it to PDF or HTML

Just tell me what you need next. 

You said:
Make it all txt only copy by my self
ChatGPT said:
Below is the FULL TUTORIAL IN PLAIN TEXT ONLY
(no Markdown, no formatting tricks — you can copy-paste it anywhere)

Debian 9 (Stretch) – Full LAMP Stack Installation Tutorial

LAMP = Linux + Apache + MySQL/MariaDB + PHP

This guide explains how to install and configure a complete LAMP stack on Debian 9 (Stretch).

Prerequisites

Debian 9 installed

Root access or sudo user

Internet connection

Check Debian version:

cat /etc/debian_version

Update the System

sudo apt update
sudo apt upgrade -y

Optional but recommended:

sudo apt install -y apt-transport-https ca-certificates curl

Install Apache Web Server

Install Apache:

sudo apt install -y apache2

Start and enable Apache:

sudo systemctl start apache2
sudo systemctl enable apache2

Test Apache:

Open a browser and visit:
http://your_server_ip/

You should see the Apache default page.

Useful Apache commands:

sudo systemctl status apache2
sudo systemctl restart apache2
sudo systemctl stop apache2

Install MariaDB (MySQL)

Install MariaDB server and client:

sudo apt install -y mariadb-server mariadb-client

Start and enable MariaDB:

sudo systemctl start mariadb
sudo systemctl enable mariadb

Secure MariaDB:

sudo mysql_secure_installation

Recommended answers:

Set root password: Yes

Remove anonymous users: Yes

Disallow remote root login: Yes

Remove test database: Yes

Reload privilege tables: Yes

Test database login:

mysql -u root -p

Exit MariaDB:

EXIT;

Install PHP 7.0

Install PHP and common extensions:

sudo apt install -y php php-mysql php-cli php-curl php-gd php-mbstring php-xml php-zip libapache2-mod-php

Verify PHP installation:

php -v

Configure Apache for PHP

Enable PHP module:

sudo a2enmod php7.0
sudo systemctl restart apache2

Edit directory index priority:

sudo nano /etc/apache2/mods-enabled/dir.conf

Change the line to:

DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm

Restart Apache:

sudo systemctl restart apache2

Test PHP

Create PHP test file:

sudo nano /var/www/html/info.php

Add this content:

<?php phpinfo(); ?>
Open in browser:

http://your_server_ip/info.php

If PHP info page appears, PHP is working.

IMPORTANT: Remove the file after testing:

sudo rm /var/www/html/info.php

Create Apache Virtual Host

Create website directory:

sudo mkdir -p /var/www/example.com/public_html
sudo chown -R www-data:www-data /var/www/example.com
sudo chmod -R 755 /var/www/example.com

Create virtual host config:

sudo nano /etc/apache2/sites-available/example.com.conf

Paste this configuration:

<VirtualHost *:80>
ServerName example.com
ServerAlias www.example.com
DocumentRoot /var/www/example.com/public_html

<Directory /var/www/example.com/public_html>
    AllowOverride All
    Require all granted
</Directory>

ErrorLog ${APACHE_LOG_DIR}/example.com_error.log
CustomLog ${APACHE_LOG_DIR}/example.com_access.log combined
</VirtualHost>
Enable virtual host and disable default site:

sudo a2ensite example.com.conf
sudo a2dissite 000-default.conf
sudo systemctl reload apache2

Test PHP in Virtual Host

Create test PHP file:

sudo nano /var/www/example.com/public_html/index.php

Add:

<?php echo "LAMP Stack is working!"; ?>
Visit in browser:

http://example.com

Firewall Configuration (Optional)

Install UFW:

sudo apt install -y ufw

Allow SSH and Apache:

sudo ufw allow OpenSSH
sudo ufw allow Apache Full

Enable firewall:

sudo ufw enable

Check firewall status:

sudo ufw status

Important Paths

Web root:
/var/www/html

Apache configuration:
/etc/apache2/

Virtual hosts:
/etc/apache2/sites-available/

PHP configuration:
/etc/php/7.0/apache2/php.ini

MariaDB data directory:
/var/lib/mysql

Final Verification

apache2 -v
php -v
mysql --version

Debian 9 LAMP stack installation is now complete.





