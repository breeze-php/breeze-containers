FROM centos:7

RUN yum clean all
RUN yum -y update
RUN yum -y install epel-release
RUN rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm

RUN yum -y groupinstall "Development Tools"

RUN yum -y install \
        openssl-devel \
        php71w-pear \
        php71w-devel \
        php71w-fpm \
        php71w-cli \
        php71w-mbstring

RUN yum -y install vim lynx

RUN pecl install mongodb-1.2.8

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

COPY etc/php.ini /etc/php.ini
COPY etc/php.d/mongo.ini /etc/php.d/mongo.ini

COPY etc/php-fpm.conf /etc/php-fpm.conf
COPY etc/php-fpm.d/www.conf /etc/php-fpm.d/www.conf

CMD php-fpm

EXPOSE 9000
