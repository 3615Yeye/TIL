# Set up a reverse proxy for a node.js app (http traffic only)
To be done as root or with sudo.

## Activate necessary modules
a2enmod proxy proxy_http

## App configuration for apache
cd /etc/apache2/sites-available/
vim myapp.conf
    <VirtualHost *:80>
            ServerName www.mydomain.com

            ProxyRequests Off

            ProxyPass / http://127.0.0.1:8080/
            ProxyPassReverse / http://0.0.0.0:8080/

            ErrorLog ${APACHE_LOG_DIR}/error.log
    </VirtualHost>

a2ensite myapp.conf

service apache2 restart
