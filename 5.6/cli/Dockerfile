FROM debian:jessie
LABEL maintainer "open-source@scott-weldon.com"

ARG last-apt-update=2017-03-06
RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y php5-cli

ENTRYPOINT ["php"]
CMD ["-a"]
