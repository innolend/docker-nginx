# Docker Nginx

This is images based on `alpine` linux and configured to work with php-fpm host by the default

## Nginx for usage with php-fpm

### Connecting guide
To connect the nginx to yours compose, you just need to add following lines to yours compose file

```
intvoice-www:
    image: innolend/nginx
    hostname: intvoice-server
    links:
      - intvoice-php:php-fpm-host
    depends_on:
      - intvoice-php
    volumes:
      - ./:/var/www/html
      - ./docker/nginx:/etc/nginx/conf.d      
      - ./docker/logs/nginx:/var/log/nginx
    ports:
        - "80:80"
```

Where intvoice-php is `innolend/php` container