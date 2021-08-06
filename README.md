# Sivujetti SDK

Tools that helps you write Sivujetti sites and themes.

## Build notes macos

...

### Backend tools (php)

See also php-src/azure/macos/job.yml.

1. Dowload php-src
1. Install deps
	- brew install pkg-config \
                   autoconf \
                   bison \
                   re2c
    - brew install openssl@1.1 \
                   icu4c \
                   libiconv \
                   gd \
                   libzip \
                   libxml2
1. `cd php-src`
1. Prepare
	- `mkdir mydir`
	- `rm configure`
	- `./buildconf --force`
	- `export PKG_CONFIG_PATH="/usr/local/opt/icu4c/lib/pkgconfig"`
1. Configure
	- ./configure \
  --prefix=/path/to/php-src/mydir \
  --disable-debug \
  --enable-mbstring \
  --enable-intl \
  --with-zip \
  --with-curl \
  --with-sodium \
  --with-iconv=/usr/local/opt/libiconv
1. Monkey patch phpinfo()
    - `sed -i -e '/CONFIGURE_COMMAND/s/^/\/\/ /g' main/build-defs.h`
    - `sed -i -e '/PHP_BUILD_SYSTEM/s/^/\/\/ /g' main/php_config.h`
1. Install
    - `make -j$(sysctl -n hw.ncpu)`
    - `make install`

## Xdebug

See also https://xdebug.org/docs/install#compile.

- /path/to/php-src/mydir/bin/phpize
- ./configure --enable-xdebug --with-php-config=/path/to/php-src/mydir/bin/php-config
- make
- make install
- cp modules/xdebug.so /path/to/php-src/mydir/lib/php/extensions/no-debug-non-zts-20200930/xdebug.so

### Create zip

todo

## Frontend tools

todo
