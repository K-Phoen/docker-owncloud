FROM resin/rpi-raspbian

MAINTAINER Kévin Gomez <contact@kevingomez.fr>

RUN mkdir -p /var/www/owncloud/data
RUN chmod -R 0777 /var/www/owncloud/data
RUN chown -R www-data:www-data /var/www/owncloud/data
VOLUME ["/var/www/owncloud/data"]

RUN mkdir -p /var/www/owncloud/config
RUN chmod -R 0777 /var/www/owncloud/config
RUN chown -R www-data:www-data /var/www/owncloud/config
VOLUME ["/var/www/owncloud/config"]

CMD echo "Data container only (/data, /config)"
