# How to use

``` console
$ docker run --name server-centos7 -d centos7-webserver-oracle
```

## Centos7
Using [`centos:centos7`](https://hub.docker.com/_/centos)

Webserver use [`httpd`](https://httpd.apache.org/download.cgi), [`php7.4`](https://www.php.net/downloads.php)

Extension php7.4 default:
```
php-bcmath, php-cli, php-common, php-devel, php-fileinfo, php-gd, php-intl, php-ldap, php-mbstring, php-pear, php-soap, php-xml, php-xmlrpc, php-zip
```

Remote centos7
```console
$ docker exec -it centos /bin/sh
```

Lookup oracle ip address
``` console
$ docker inspect oracle | grep IPAddress
```

## Oracle 11g

See reference [`oracleinanutshell:oracle-xe-11g.`](https://hub.docker.com/r/oracleinanutshell/oracle-xe-11g)

By default setting :

```
hostname: localhost
port: 1521
sid: xe
username: system
password: oracle
```