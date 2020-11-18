FROM centos:centos7

RUN echo 'running webserver install'

# Install httpd
RUN yum -y update
RUN yum -y install httpd 

# Install remi
RUN rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm \
    && rpm -Uvh http://rpms.remirepo.net/enterprise/remi-release-7.rpm

RUN yum install yum-utils
RUN yum-config-manager --enable remi-php74


# Install extension
RUN yum --enablerepo=remi-php74 -y install libaio make php php-bcmath php-cli php-common php-devel php-fileinfo php-gd php-intl php-ldap php-mbstring \
    php-pear php-soap php-xml php-xmlrpc php-zip systemtap-sdt-devel

CMD ["rpm", "-ivh", "./instantclient/oracle-*.rpm"]

RUN export PHP_DTRACE=yes && ldconfig && echo '' | pecl install oci8

RUN echo extension=oci8 >> /etc/php.ini

RUN sed -E -i -e '/<Directory "\/var\/www\/html">/,/<\/Directory>/s/AllowOverride None/AllowOverride All/' /etc/httpd/conf/httpd.conf
RUN sed -E -i -e 's/DirectoryIndex (.*)$/DirectoryIndex index.php \1/g' /etc/httpd/conf/httpd.conf

# Update Apache Configuration
EXPOSE 80

# Start Apache
CMD ["/usr/sbin/httpd","-D","FOREGROUND"]

