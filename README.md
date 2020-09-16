# PHP Local Development

## Setup environment

## Create website configuration
1. Create a configurate file /etc/nginx/sites-available/website.local
```bash
sudo touch /etc/nginx/sites-available/website.local
```
2. Copy entry of **nginx-site-conf-example** into /etc/nginx/sites-available/website.local and edit it
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
