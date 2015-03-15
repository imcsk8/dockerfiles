FROM imcsk8/fedora-21
MAINTAINER Ivan Chavero "imcsk8@sotoliolabs.com"

# Change this for the ip address of the standalone
# fastcgi server

RUN yum install -y nginx tar bzip2
RUN groupadd owncloud-user
RUN useradd -g owncloud-user -c 'OwnCloud User' -s /bin/false -d /var/www owncloud-user

RUN curl https://download.owncloud.org/community/owncloud-latest.tar.bz2 > owncloud-latest.tar.bz2
RUN tar jxf owncloud-latest.tar.bz2 -C /var/www 
RUN rm -f owncloud-latest.tar.bz2

ADD resources/start.sh /
ADD resources/php-fpm /
ADD resources/nginx /
ADD resources/nginx.conf /etc/nginx/

RUN chown -R owncloud-user:owncloud-user /var/www/
RUN chmod +x /start.sh

# Define mountable directories.

CMD ["/start.sh"]

