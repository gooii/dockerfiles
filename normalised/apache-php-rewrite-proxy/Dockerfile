FROM php:5.6-apache

MAINTAINER Martin Wood-Mitrovski martin.wood@gooii.com

COPY apache.conf /etc/apache2/apache.conf

RUN a2enmod proxy proxy_http rewrite ssl

RUN service apache2 restart
