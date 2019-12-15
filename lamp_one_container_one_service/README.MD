# Create LAMP stack(one service one container)
    
go to folder "lamp_one_container_one_service" and run command in your terminal
for apache (https://hub.docker.com/_/httpd)
`docker run -dit --name my-apache-app -p 8080:80 -v "$PWD/src":/usr/local/apache2/htdocs/ httpd:2.4`
for php-fpm (https://hub.docker.com/_/php) 7.3.12-fpm-buster
`docker run -dit --name my-php-fpm -p 9001:9000 -v "$PWD/src":/var/www/html php:7.3.12-fpm-buster` 
next step go to apache container `docker exec -it my-apache-app bash` and add upstream for php-fpm container 
in /usr/local/aoache2/conf/httpd.conf (https://cwiki.apache.org/confluence/display/HTTPD/PHP-FPM)
`docker cp apache/httpd.conf my-apache-app:/usr/local/apache2/conf/httpd.conf`
in this file added and load mod_proxy and mod_proxy_fcgi
```bash
 <FilesMatch \.php$>
        SetHandler "proxy:fcgi://127.0.0.1:9001"
  </FilesMatch>
```