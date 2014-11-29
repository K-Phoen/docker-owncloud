FROM resin/rpi-raspbian
MAINTAINER Kévin Gomez <contact@kevingomez.fr>

ENV DEBIAN_FRONTEND noninteractive

# essential tools
RUN apt-get update -y
RUN apt-get install -y curl supervisor bzip2

# Use supervisord as init system
ADD config/supervisor.conf /etc/supervisor/conf.d/supervisor.conf
ADD init.sh /init.sh
CMD ["/usr/bin/supervisord"]

# install PHP
RUN apt-get install -y php5 php5-cli php5-sqlite php5-curl php5-gd php5-mcrypt php5-intl php5-fpm php5-json php5-mysqlnd php5-imagick php5-apcu
RUN sed -e 's/;daemonize = yes/daemonize = no/' -i /etc/php5/fpm/php-fpm.conf
RUN sed -e 's/;listen\.owner/listen.owner/' -i /etc/php5/fpm/pool.d/www.conf
RUN sed -e 's/;listen\.group/listen.group/' -i /etc/php5/fpm/pool.d/www.conf
ADD config/php_custom.ini /etc/php5/mods-available/custom.ini
RUN php5enmod custom

# install nginx
RUN apt-get install -y nginx
ADD config/vhost.conf /etc/nginx/sites-available/default
ADD config/nginx.conf /etc/nginx/nginx.conf

# install owncloud
RUN curl -k https://download.owncloud.org/community/owncloud-7.0.2.tar.bz2 | tar jx -C /var/www/
RUN chown -R www-data:www-data /var/www/owncloud

# install mysql
RUN apt-get install -y mysql-server

# Clean up APT when done.
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN chmod +x /init.sh

EXPOSE 80
