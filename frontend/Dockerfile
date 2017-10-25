FROM ubuntu:latest

RUN apt-get update \
    && apt-get install -y software-properties-common language-pack-en-base && LC_ALL=en_US.UTF-8 add-apt-repository ppa:ondrej/php && apt-get update \
    && apt-get install -y php5.6 php5.6-mysqli php5.6-mcrypt php5.6-gd \
       php5.6-curl php5.6-redis php5.6-mbstring supervisor \
       php5.6-fileinfo php5.6-gd php5.6-gettext php5.6-intl \
       php5.6-exif php5.6-soap  \
       php5.6-xmlrpc php5.6-xsl php5.6-apcu php5.6-mongo php5.6-mongodb \
       php5.6-memcache \
    && apt-get install -y npm \
    && apt-get install -y ruby \
    && apt-get install -y ruby-compass \
    && apt-get install -y build-essential \
    && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
    && update-alternatives --set php /usr/bin/php5.6

RUN gem install sass

RUN npm install gulp -g && npm install bower -g && npm install typescript -g && npm install typings -g

WORKDIR /var/www/influencing

RUN ln -s /usr/bin/nodejs /usr/bin/node

RUN echo '{ "allow_root": true }' > /root/.bowerrc

EXPOSE 3030
EXPOSE 35729

ENTRYPOINT . docs/dev.sh
