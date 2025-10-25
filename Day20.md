# Configure Nginx + PHP-FPM Using Sock

## Question
```bash
The Nautilus application development team is planning to launch a new PHP-based application, which they want to deploy on Nautilus infra in Stratos DC. The development team had a meeting with the production support team and they have shared some requirements regarding the infrastructure. Below are the requirements they shared:



a. Install nginx on app server 3 , configure it to use port 8097 and its document root should be /var/www/html.


b. Install php-fpm version 8.1 on app server 3, it must use the unix socket /var/run/php-fpm/default.sock (create the parent directories if don't exist).


c. Configure php-fpm and nginx to work together.


d. Once configured correctly, you can test the website using curl http://stapp03:8097/index.php command from jump host.

NOTE: We have copied two files, index.php and info.php, under /var/www/html as part of the PHP-based application setup. Please do not modify these files.

```

## Solution

### Install nginx

- sudo yum install nginx -y

### Configure nginx to listen on custom port 

- sudo vi /etc/nginx/nginx.conf

find the server block or modify /etc/nginx/conf.f/default.conf if exist.

Change or add this block:

```bash 
server {
    listen 8097;
    server_name localhost;

    root /var/www/html;
    index index.php index.html index.htm;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include fastcgi_params;
        fastcgi_pass unix:/var/run/php-fpm/default.sock;
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    }
}
```

### Install PHP-FPM 8.1

- For CentOS 8

```bash
sudo yum install -y https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm
sudo yum install -y https://rpms.remirepo.net/enterprise/remi-release-8.rpm
```

- For centOS stream 9

```bash
sudo yum install -y https://dl.fedoraproject.org/pub/epel/epel-release-latest-9.noarch.rpm
sudo yum install -y https://rpms.remirepo.net/enterprise/remi-release-9.rpm
```

### Configure PHP-FPM to use custom socket

- sudo vi /etc/php-fpm.d/www.conf

Modify `listen` to:
- listen = /var/run/php-fpm/default.sock

### Make sure directory exist

- sudo mkdir -p /var/run/php-fpm
- sudo chown -R nginx:nginx /var/run/php-fpm

### Confirm `php-fpm` runs as thesame user as `nginx`

- ls -l /var/run/php-fpm/default.sock

### Start and Enable both service 

php-fpm

- sudo systemctl enable php-fpm
- sudo systemctl start php-fpm
- sudo systemctl status php-fpm

Nginx

- sudo systemctl enable nginx 
- sudo systemctl start nginx
- sudo systemctl status nginx


### Test the Setup from Jump Host:

- curl http://stapp03:8097/index.php

