FROM bitnami/minideb-extras:jessie-r103
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages libbz2-1.0 libc6 libcomerr2 libcurl3 libexpat1 libffi6 libfreetype6 libgcc1 libgcrypt20 libgmp10 libgnutls-deb0-28 libgpg-error0 libgssapi-krb5-2 libhogweed2 libicu52 libidn11 libjpeg62-turbo libk5crypto3 libkeyutils1 libkrb5-3 libkrb5support0 libldap-2.4-2 liblzma5 libmcrypt4 libncurses5 libnettle4 libp11-kit0 libpcre3 libpng12-0 libpq5 libreadline6 librtmp1 libsasl2-2 libsqlite3-0 libssh2-1 libssl1.0.0 libstdc++6 libsybdb5 libtasn1-6 libtidy-0.99-0 libtinfo5 libxml2 libxslt1.1 zlib1g
RUN bitnami-pkg unpack apache-2.4.33-4 --checksum f26751a96abdc45db43c4b92eb9f792a4b630ad0edd5667aa73ccafa0aeb3810
RUN bitnami-pkg unpack php-7.0.30-8 --checksum c9bcf8d4c9c280645e44de07ae4a0e8d436333688094d5587b4b0766036cff8a
RUN bitnami-pkg unpack mysql-client-10.1.34-0 --checksum 2954d9390cb8b91dc924beacc179ed03050f6c5cb7ad328010cdbde1ab05c1e9
RUN bitnami-pkg install libphp-7.0.30-8 --checksum 0fb74a5477bdf72ee85751af91ee2e41beec5b18657a9891d7081a3e2ce7289e
RUN bitnami-pkg unpack matomo-3.5.1-0 --checksum 165c7828d3f32945d5601bd5e43e22c0a7ebb99c227690e36eb61b57950a5e75

COPY rootfs /
ENV ALLOW_EMPTY_PASSWORD="no" \
    APACHE_HTTPS_PORT_NUMBER="443" \
    APACHE_HTTP_PORT_NUMBER="80" \
    BITNAMI_APP_NAME="matomo" \
    BITNAMI_IMAGE_VERSION="3.5.1-debian-8-r15" \
    MARIADB_HOST="mariadb" \
    MARIADB_PORT_NUMBER="3306" \
    MARIADB_ROOT_PASSWORD="" \
    MARIADB_ROOT_USER="root" \
    MATOMO_DATABASE_NAME="bitnami_matomo" \
    MATOMO_DATABASE_PASSWORD="" \
    MATOMO_DATABASE_USER="bn_matomo" \
    MATOMO_EMAIL="user@example.com" \
    MATOMO_HOST="127.0.0.1" \
    MATOMO_PASSWORD="bitnami" \
    MATOMO_USERNAME="User" \
    MATOMO_WEBSITE_HOST="https://example.org" \
    MATOMO_WEBSITE_NAME="example" \
    MYSQL_CLIENT_CREATE_DATABASE_NAME="" \
    MYSQL_CLIENT_CREATE_DATABASE_PASSWORD="" \
    MYSQL_CLIENT_CREATE_DATABASE_PRIVILEGES="ALL" \
    MYSQL_CLIENT_CREATE_DATABASE_USER="" \
    PATH="/opt/bitnami/apache/bin:/opt/bitnami/php/bin:/opt/bitnami/php/sbin:/opt/bitnami/mysql/bin:$PATH" \
    SMTP_HOST="" \
    SMTP_PASSWORD="" \
    SMTP_PORT="" \
    SMTP_PROTOCOL="" \
    SMTP_USER=""

EXPOSE 80 443

ENTRYPOINT ["/app-entrypoint.sh"]
CMD ["nami","start","--foreground","apache"]
