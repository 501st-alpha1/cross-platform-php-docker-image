FROM 501stalpha1/php:5.6-cli
LABEL maintainer "open-source@scott-weldon.com"

ARG last-apt-update=2017-03-07
RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y apache2 libapache2-mod-php5

COPY apache2-foreground /usr/local/bin/

EXPOSE 80
ENTRYPOINT ["apache2-foreground"]
