FROM ubuntu:latest

RUN apt-get update && apt-get install -y software-properties-common language-pack-en-base \
    && LC_ALL=en_US.UTF-8 add-apt-repository -y ppa:ondrej/php \
    && apt-get update \
    && apt-get install -y php5.6 php5.6-fpm php5.6-mysqli php5.6-mcrypt php5.6-gd \
       php5.6-curl php5.6-redis php5.6-mbstring supervisor \
       php5.6-fileinfo php5.6-gd php5.6-gettext php5.6-intl \
       php5.6-exif php5.6-soap  \
       php5.6-xmlrpc php5.6-xsl php5.6-apcu php5.6-mongo php5.6-mongodb \
       php5.6-memcache \
    && mkdir /run/php \
    && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
    && update-alternatives --set php /usr/bin/php5.6

COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

RUN sed -i -e 's/listen = \/run\/php\/php5.6-fpm.sock/listen = 0.0.0.0:9000/g' /etc/php/5.6/fpm/pool.d/www.conf \
    && sed -i -e 's/;daemonize = yes/daemonize = no/g' /etc/php/5.6/fpm/php-fpm.conf

WORKDIR /var/www/

CMD ["/usr/bin/supervisord"]
