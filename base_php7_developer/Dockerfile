FROM kagomema24/docker-images:base_php7
MAINTAINER Simon Ball <open-source@simonball.me>

USER root

RUN apk --update add \
  # EXTRA DEVELOPER TOOLS
  php7-fileinfo \
  php7-pear \
  php7-simplexml \
  php7-tokenizer \
  php7-xdebug \
  php7-xsl \
  php7-pcntl \
  php7-sockets \
  php7-sysvsem \
  nodejs \
  nodejs-npm \
  shadow \
  && rm -rf /var/cache/apk/*

# Enable xDebug
RUN echo "zend_extension=xdebug.so" > /etc/php7/conf.d/xdebug.ini

# Copy across some of the utilities
COPY tools/pdepend /usr/local/bin/pdepend
COPY tools/phpcbf /usr/local/bin/phpcbf
COPY tools/phpcpd /usr/local/bin/phpcpd
COPY tools/phpcs /usr/local/bin/phpcs
COPY tools/phpdox /usr/local/bin/phpdox
COPY tools/phploc /usr/local/bin/phploc
COPY tools/phpmd /usr/local/bin/phpmd
COPY tools/phpunit /usr/local/bin/phpunit
COPY usergroup.sh /usr/local/bin/usergroupmatch

# Output the versions os the above utilities
RUN chmod a+x -R /usr/local/bin

# GulpJS task runner
RUN npm i -g \
    bower \
    gulp \
    gulp-cli \
    grunt-cli \
    marked \
    node-gyp \
    webpack \
    yarn

CMD ["/bin/bash"]
