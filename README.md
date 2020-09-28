# PHP Local Development

## Setup LEMP stack
### Step 1: Update Software Packages
```bash
sudo apt update
sudo apt upgrade
```
### Step 2: Install Nginx Web Server
```bash
sudo apt install nginx -y
sudo systemctl enable nginx
sudo systemctl start nginx
sudo systemctl status nginx
```
```
for i in ssh http https
do
           ufw allow $i
done
```
```bash
ufw enable
```
### Step 3: Install MariaDB Database Server
```bash
sudo apt-get install mariadb-server mariadb-client
sudo mysql_secure_installation
```
When prompted, answer the questions below by following the guide.
Enter current password for root (enter for none): Just press the Enter
* Set root password? [Y/n]: Y
* New password: Enter password
* Re-enter new password: Repeat password
* Remove anonymous users? [Y/n]: Y
* Disallow root login remotely? [Y/n]: Y
* Remove test database and access to it? [Y/n]:  Y
* Reload privilege tables now? [Y/n]:  Y
To verify and validate that MariaDB is installed and working, login to the database console using the commands below:
```bash
sudo mysql -u root -p
```
```sql
MariaDB [(none)]> GRANT ALL ON example_database.* TO 'admin'@'localhost' IDENTIFIED BY 'admin' WITH GRANT OPTION;
MariaDB [(none)]> FLUSH PRIVILEGES;
MariaDB [(none)]> exit;
```
### Step 4: Install PHP 7.4 and Related Modules
```bash
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:ondrej/php
sudo apt update
sudo apt install php7.4-fpm php7.4-common php7.4-mysql php7.4-gmp php7.4-curl php7.4-intl php7.4-mbstring php7.4-xmlrpc php7.4-gd php7.4-xml php7.4-cli php7.4-zip php7.4-sqlite3
sudo nano /etc/php/7.4/fpm/php.ini
```
```ini
file_uploads = On
allow_url_fopen = On
short_open_tag = On
memory_limit = 256M
cgi.fix_pathinfo = 0
upload_max_filesize = 100M
max_execution_time = 360
date.timezone = Europe/Kiev
```

## Create website configuration
1. Create a configurate file /etc/nginx/sites-available/website.local
```bash
sudo touch /etc/nginx/sites-available/website.local
```
2. Copy entry of [nginx-site-conf-example](https://github.com/bvlad05/php-local-development/blob/master/nginx-website-conf-example) into /etc/nginx/sites-available/website.local and edit it
```bash
sudo nano /etc/nginx/sites-available/website.local
```
3. Create a symbolic link
```bash
sudo ln -s /etc/nginx/sites-available/website.local /etc/nginx/sites-enabled/
```
4. Add local domain into the hosts
```bash
sudo nano /etc/hosts
```
And add next line
```
127.0.0.1  website.local
```
5. Reload nginx service
```bash
sudo systemctl restart nginx.service
```
6. Create project folder with permissions
```bash
cd ~/Projects
sudo mkdir website
sudo chown -R www-data:www-data website/
sudo chmod -R 775 website/
```
