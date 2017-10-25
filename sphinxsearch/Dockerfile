FROM phusion/baseimage

RUN apt-get update \
    && apt-get -y install software-properties-common \
    && apt-get update \
    && add-apt-repository -y ppa:builds/sphinxsearch-beta \
    && apt-get update \
    && apt-get -y install sphinxsearch \
    && mkdir /var/lib/sphinx \
    && mkdir /var/lib/sphinx/data \
    && mkdir /var/log/sphinx \
    && mkdir /var/run/sphinx

ADD indexandsearch.sh /
RUN chmod a+x indexandsearch.sh
ADD searchd.sh /
RUN chmod a+x searchd.sh

