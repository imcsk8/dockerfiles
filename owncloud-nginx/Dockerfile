FROM imcsk8/fedora-21
MAINTAINER Ivan Chavero "imcsk8@sotoliolabs.com"

# Change this for the ip address of the standalone
# fastcgi server

RUN yum install -y yum-fastestmirror yum-presto deltarpm nginx tar bzip2 php php-fpm openssl smbclient php-pdo supervisor
RUN groupadd owncloud-user
RUN useradd -g owncloud-user -c 'OwnCloud User' -s /bin/false -d /var/www owncloud-user

RUN curl https://download.owncloud.org/community/owncloud-latest.tar.bz2 > owncloud-latest.tar.bz2
RUN tar jxf owncloud-latest.tar.bz2 -C /var/www 
RUN rm -f owncloud-latest.tar.bz2

ADD resources/nginx.conf /etc/nginx/nginx.conf
ADD resources/supervisord.conf /etc/supervisor/supervisord.conf
ADD resources/www.conf /etc/php-fpm.d/www.conf
ADD resources/start.sh /start.sh

RUN chown -R owncloud-user:owncloud-user /var/www/

CMD ["/start.sh"]
