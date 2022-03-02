## Description

Minimal PHP Docker image focused on AdminControl application. This docker image is based on KOOL.dev's [docker-php](https://github.com/kool-dev/docker-php) images.

## Environment Variables

Variable | Default Value | Description
--- | --- | ---
**ASUSER** | `0` | Changes the user id that executes the commands
**UID** | `0` | Changes the user id that executes the commands **(ignored if ASUSER is provided)**
**COMPOSER_ALLOW_SUPERUSER** | `1` | Allows composer to run with super user
**COMPOSER_MEMORY_LIMIT** | `-1` | Changes composer memory limit
**ENABLE_XDEBUG** | `false` | Enables the Xdebug extension
**PHP_DATE_TIMEZONE** | `UTC` | Changes timezone used by date/time functions
**PHP_MEMORY_LIMIT** | `256M` | Changes PHP memory limit
**PHP_MAX_INPUT_VARS** | `1000`  | Changes how many input variables may be accepted on PHP
**PHP_UPLOAD_MAX_FILESIZE** | `25M` | Changes PHP maximum size of an uploaded file
**PHP_POST_MAX_SIZE** | `25M` | Changes PHP max size of post data allowed
**PHP_MAX_EXECUTION_TIME** | `30` | Changes PHP maximum time is allowed to run a script
**PHP_FPM_LISTEN** | `9000` | Changes the PORT address of the FastCGI requests
**PHP_FPM_MAX_CHILDREN** | `10` | Changes the number of child processes to be used on FPM
**PHP_FPM_REQUEST_TERMINATE_TIMEOUT** | `60` | Changes FPM timeout to serve a single request

### NGINX

Variable | Default Value | Description
--- | --- | ---
**NGINX_LISTEN** | `80` | Changes the PORT address
**NGINX_ROOT** | `/app/public` | Changes NGINX root directive
**NGINX_INDEX** | `index.php` | Changes the index directive
**NGINX_CLIENT_MAX_BODY_SIZE** | `25M` | Changes maximum allowed size of the client request body
**NGINX_PHP_FPM** | `unix:/run/php-fpm.sock` | Changes the address of a FastCGI server
**NGINX_FASTCGI_READ_TIMEOUT** | `60s` | Changes a timeout for reading a response from the FastCGI server
**NGINX_FASTCGI_BUFFERS** | `8 8k` | Changes the number and size of the buffers used for reading a response
**NGINX_FASTCGI_BUFFER_SIZE** | `16k` | Changes the size of the buffer used for reading the first part of the response received

## Usage

With `docker run`:

```sh
docker run -it --rm jozefrebjak/admincontrol:PHP-8.0 php -v
```

With environment variables:

```sh
docker run -it --rm -e ENABLE_XDEBUG=true jozefrebjak/admincontrol:PHP-8.0 php -v
```

With `docker-compose.yml`:

```yaml
app:
  image: jozefrebjak/admincontrol:PHP-8.0
  ports:
    - "9000:9000"
  volumes:
    - ".:/app:cached"
    - "$HOME/.ssh/id_rsa:/home/developer/.ssh/id_rsa:cached"
  environment:
    ASUSER: "${$UID}"
```

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.