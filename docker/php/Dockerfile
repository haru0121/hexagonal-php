# イメージを取得
FROM php:8.0-fpm
# 独自のphp.iniファイル(PHPの設定ファイル)を
# コンテナ内の/usr/local/etc/php/ディレクトリにコピー
COPY php.ini /usr/local/etc/php/

# パッケージやPHPの拡張モジュールをインストールするコマンド　を実行
RUN apt-get update && apt-get install -y \
	git \
	curl \
	zip \
	unzip \
    && docker-php-ext-install pdo_mysql

# xdebugのインストール
RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

# 作業ディレクトリを/var/wwwに設定
WORKDIR /var/www/html
COPY --from=composer /usr/bin/composer /usr/bin/composer
ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer