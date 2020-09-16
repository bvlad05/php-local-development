# PHP Local Development

## Setup LEMP stack
### Step 1: Update Software Packages
```bash
sudo apt update
sudo apt upgrade
```
### Step 2: Install Nginx Web Server
```bash
sudo apt install nginx
sudo systemctl enable nginx
sudo systemctl start nginx
sudo systemctl status nginx
```
### Step 1: Update Software Packages
```bash

```
### Step 1: Update Software Packages
```bash

```
### Step 1: Update Software Packages
```bash

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
sudo systemctl reload nginx.service
```
6. Create project folder with permissions
```bash
cd ~/Projects
sudo mkdir website
sudo chown -R www-data:www-data website/
sudo chmod -R 775 website/
```
