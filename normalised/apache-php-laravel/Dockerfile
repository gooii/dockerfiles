FROM tutum/apache-php:latest

RUN apt-get update
RUN apt-get install -yq php5-mcrypt
RUN a2enmod rewrite
RUN php5enmod mcrypt
RUN service apache2 restart
