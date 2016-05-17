FROM php:5.6
MAINTAINER Johannes Schickling "schickling.j@gmail.com"

# Install mbstring php extension using php image's docker-php-ext-install method described here https://hub.docker.com/_/php/
# Without mbstring the "Add job" functionality will error with "Call to undefined function mb_strlen()"
RUN docker-php-ext-install mbstring

ADD install.sh install.sh
RUN chmod +x install.sh && ./install.sh && rm install.sh

EXPOSE 2080
CMD bash -c 'BEANSTALK_SERVERS=$BEANSTALKD_PORT_11300_TCP_ADDR:11300 php -S 0.0.0.0:2080 -t /source/public'
