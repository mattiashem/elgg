from ubuntu:rolling
RUN apt-get update
RUN apt-get install apache2 wget unzip -y
RUN apt-get install php libapache2-mod-php php-mysql php-gd php-dom -y
RUN a2enmod rewrite


RUN mkdir -p /var/elgg/data
RUN chmod 777 /var/elgg/data

WORKDIR /var/www/html
RUN  wget https://elgg.org/getelgg.php?forward=elgg-2.3.3.zip
RUN unzip *.zip
RUN rm -f *.zip
RUN mv elgg-* elgg
RUN chown www-data:www-data -R /var/www/html/elgg
RUN chmod 774 -R /var/www/html/elgg

ADD elgg.conf /etc/apache2/sites-enabled/elgg.conf
RUN rm -f /etc/apache2/sites-enabled/000-default.conf


CMD apachectl -DFOREGROUND
