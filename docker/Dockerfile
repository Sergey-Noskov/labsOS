FROM debian
ADD debian.list /etc/apt/sources.list.d/
RUN apt-get update && apt-get -y upgrade && apt -y install nginx && apt-get clean && \
    cd /var/www/ && rm -rf ./* && \
    mkdir -p sergey.com/img && \
    chmod -R 754 /var/www/sergey.com/ && \
    useradd sergey && groupadd standart && usermod -aG standart sergey && \
    chown -R sergey:standart /var/www/sergey.com/ && \
    sed -i 's/\/var\/www\/html/\/var\/www\/sergey.com/g' /etc/nginx/sites-enabled/default && \
    sed -i 's/user www-data/user sergey/g' /etc/nginx/nginx.conf
ADD index.html /var/www/sergey.com/
ADD Screen2.0.jpg /var/www/sergey.com/img/
CMD ["nginx", "-g", "daemon off;"]
