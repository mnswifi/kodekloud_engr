# Install and Configure Web Application

## Question:

```bash
xFusionCorp Industries is planning to host two static websites on their infra in Stratos Datacenter. The development of these websites is still in-progress, but we want to get the servers ready. Please perform the following steps to accomplish the task:



a. Install httpd package and dependencies on app server 2.


b. Apache should serve on port 3003.


c. There are two website's backups /home/thor/official and /home/thor/games on jump_host. Set them up on Apache in a way that official should work on the link http://localhost:3003/official/ and games should work on link http://localhost:3003/games/ on the mentioned app server.


d. Once configured you should be able to access the website using curl command on the respective app server, i.e curl http://localhost:3003/official/ and curl http://localhost:3003/games/
```

## Solution

### Install httpd

- Sudo yum install httpd -y
- sudo systemctl enable httpd

### Modify listen via:

sudo vi /etc/httpd/conf/httpd.conf


### Copy from host PC to app server

scp -r /path user@servername:/tmp/ 

- scp -r /home/thor/official steve@stapp02:/tmp/
- scp -r /home/thor/games steve@stapp02:/tmp/

### Login back to App server and move to /var/www/html

- sudo mv -R /tmp/official /var/www/html
- sudo mv -R /tmp/games /var/www/html

### Set permissions

- sudo chown -R apache:apache /var/www/html/official /var/www/html/games
- sudo chmod -R 755 /var/www/html/official /var/www/html/games

### Configure Apache to server 2 sites 

- sudo vi /etc/httpd/conf/httpd.conf

### Add configuration <Directory> to the eof

```bash
# Official website configuration
Alias /official /var/www/html/official
<Directory /var/www/html/official>
    Options Indexes FollowSymLinks
    AllowOverride None
    Require all granted
</Directory>

# Games website configuration
Alias /games /var/www/html/games
<Directory /var/www/html/games>
    Options Indexes FollowSymLinks
    AllowOverride None
    Require all granted
</Directory>
```
### Restart apache

- sudo systemctl enable httpd
- sudo systemctl restart httpd
- sudo systemctl status httpd

### If SELinux is enabled, allow apache to listen on the custom port

- sudo semanage port -a -t http_port_t -p tcp 3003

### If not enabled (semanage)

- sudo yum install -y policycoreutils-python-utils

### Verify configurations

curl http://localhost:3003/official/
curl http://localhost:3003/games/




