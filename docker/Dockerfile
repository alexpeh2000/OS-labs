FROM debian
ADD debian.list /etc/apt/sources.list.d/
RUN apt-get update && apt-get -y upgrade && apt -y install nginx && apt-get clean && \
    cd /var/www/ && rm -rf ./* && \
    mkdir -p AlexandrPekhov.com/img && \
    chmod -R 754 /var/www/AlexandrPekhov.com/ && \
    useradd Alexandr && groupadd Pekhov && usermod -aG Alexandr Pekhov && \
    chown -R Alexandr:Pekhov /var/www/AlexandrPekhov.com/ && \
    sed -i 's/\/var\/www\/html/\/var\/www\/AlexandrPekhov/g' /etc/nginx/sites-enabled/default && \
    sed -i 's/user www-data/user Alexandr/g' /etc/nginx/nginx.conf
ADD index.html /var/www/AlexandrPekhov.com/
ADD img.jpg /var/www/AlexandrPekhov.com/img/
CMD ["nginx", "-g", "daemon off;"]
