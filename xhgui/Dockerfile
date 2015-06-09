FROM torvitas/php-fpm:5.6

RUN apt-get update && apt-get install git libmcrypt-dev libgmp-dev libssh2-1-dev zlib1g-dev nginx -y --no-install-recommends && rm -r /var/lib/apt/lists/*

WORKDIR /usr/local/src
RUN git clone https://github.com/perftools/xhgui.git
RUN cd xhgui && php install.php
COPY config.default.php /usr/local/src/xhgui/config/config.php
COPY nginx.default.conf /etc/nginx/sites-available/default

VOLUME ["/usr/local/src/xhgui"]
EXPOSE 80 443
CMD ["nginx", "-g", "daemon off;"]
