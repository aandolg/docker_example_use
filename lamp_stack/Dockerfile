FROM ubuntu

RUN apt update -y
RUN apt upgrade -y
#Install apache
RUN apt install apache2 -y
#Install mysql
RUN apt install mysql-server -y
RUN service mysql start
#Install php
ENV TZ=Europe/Kiev
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt install php libapache2-mod-php php-mysql -y
COPY src/index.php /var/www/html/index.php
#COPY apache/000-default.conf /etc/apache2/sites-available/000-default.conf
#COPY apache/default-ssl.conf /etc/apache2/sites-available/default-ssl.conf
#COPY apache/apache2.conf /etc/apache2/apache2.conf
RUN rm /var/www/html/index.html
ENTRYPOINT /usr/sbin/apache2ctl -D FOREGROUND
EXPOSE 80