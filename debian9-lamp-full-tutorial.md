# Debian 9 (Stretch) – Full LAMP Stack Installation Tutorial

**LAMP = Linux + Apache + MySQL/MariaDB + PHP**

This document explains how to install and configure a complete LAMP stack on **Debian 9 (Stretch)**.

---

## 1. Prerequisites

- Debian 9 installed
- Root access or sudo privileges
- Internet connection

Check Debian version:

```bash
cat /etc/debian_version
```

---

## 2. Update the System

```bash
sudo apt update
sudo apt upgrade -y
```

Optional but recommended:

```bash
sudo apt install -y apt-transport-https ca-certificates curl
```

---

## 3. Install Apache Web Server

### 3.1 Install Apache

```bash
sudo apt install -y apache2
```

### 3.2 Start and Enable Apache

```bash
sudo systemctl start apache2
sudo systemctl enable apache2
```

### 3.3 Test Apache

Open your browser and go to:

```
http://your_server_ip/
```

You should see the Apache default page.

### 3.4 Apache Commands

```bash
sudo systemctl status apache2
sudo systemctl restart apache2
sudo systemctl stop apache2
```

---

## 4. Install MariaDB (MySQL)

### 4.1 Install MariaDB

```bash
sudo apt install -y mariadb-server mariadb-client
```

### 4.2 Start and Enable MariaDB

```bash
sudo systemctl start mariadb
sudo systemctl enable mariadb
```

### 4.3 Secure MariaDB

```bash
sudo mysql_secure_installation
```

Recommended answers:
- Set root password: Yes
- Remove anonymous users: Yes
- Disallow remote root login: Yes
- Remove test database: Yes
- Reload privilege tables: Yes

### 4.4 Test Database Login

```bash
mysql -u root -p
```

Exit:

```sql
EXIT;
```

---

## 5. Install PHP 7.0

### 5.1 Install PHP and Modules

```bash
sudo apt install -y php php-mysql php-cli php-curl php-gd php-mbstring php-xml php-zip libapache2-mod-php
```

### 5.2 Verify PHP

```bash
php -v
```

---

## 6. Configure Apache for PHP

Enable PHP module:

```bash
sudo a2enmod php7.0
sudo systemctl restart apache2
```

Edit directory index priority:

```bash
sudo nano /etc/apache2/mods-enabled/dir.conf
```

Change to:

```apache
DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
```

Restart Apache:

```bash
sudo systemctl restart apache2
```

---

## 7. Test PHP

Create PHP info file:

```bash
sudo nano /var/www/html/info.php
```

Add:

```php
<?php
phpinfo();
?>
```

Open:

```
http://your_server_ip/info.php
```

Remove after testing:

```bash
sudo rm /var/www/html/info.php
```

---

## 8. Apache Virtual Host

### 8.1 Create Website Directory

```bash
sudo mkdir -p /var/www/example.com/public_html
sudo chown -R www-data:www-data /var/www/example.com
sudo chmod -R 755 /var/www/example.com
```

### 8.2 Create Virtual Host File

```bash
sudo nano /etc/apache2/sites-available/example.com.conf
```

```apache
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
```

### 8.3 Enable Virtual Host

```bash
sudo a2ensite example.com.conf
sudo a2dissite 000-default.conf
sudo systemctl reload apache2
```

---

## 9. Test Virtual Host PHP

```bash
sudo nano /var/www/example.com/public_html/index.php
```

```php
<?php echo "LAMP Stack is working!"; ?>
```

---

## 10. Firewall (UFW)

```bash
sudo apt install -y ufw
sudo ufw allow OpenSSH
sudo ufw allow 'Apache Full'
sudo ufw enable
```

Check status:

```bash
sudo ufw status
```

---

## 11. Important Paths

- Web root: `/var/www/html`
- Apache config: `/etc/apache2/`
- Virtual hosts: `/etc/apache2/sites-available/`
- PHP config: `/etc/php/7.0/apache2/php.ini`
- MariaDB data: `/var/lib/mysql`

---

## 12. Final Verification

```bash
apache2 -v
php -v
mysql --version
```

---

**Debian 9 LAMP stack installation complete.**
