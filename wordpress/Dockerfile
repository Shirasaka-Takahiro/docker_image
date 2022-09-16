# syntax=docker/dockerfile:1.3-labs
FROM wordpress:latest
RUN apt-get update \
    && apt-get install -y vim less
RUN touch /etc/apache2/sites-enabled/vhosts.example.com.config
RUN mkdir -p /var/www/vhosts/example.com/public_html
RUN cp -ipr /var/www/html/* /var/www/vhosts/example.com/public_html
RUN find /var/www/html/ -type d -name wp-content -prune -o -type f | egrep "\.htaccess$" | xargs -I{} cp -ip {} /var/www/vhosts/example.com/public_html
COPY <<EOF /etc/apache2/sites-enabled/vhosts.example.com.config
 <VirtualHost *:80>
   ServerName example.com
   DocumentRoot /var/www/vhosts/example.com/public_html
   <Directory "/var/www/vhosts/example.com/public_html">
     AllowOverride all
     Require all granted
   </Directory>
   ErrorLog "/var/log/apache2/example.com-error_log"
   CustomLog "/var/log/apache2/example.com-access_log" common
 </VirtualHost>
EOF
