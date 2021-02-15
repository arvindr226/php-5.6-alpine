# Docker image for php-5.6-alpine.
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Farvindr226%2Fphp-5.6-alpine.svg?type=shield)](https://app.fossa.com/projects/git%2Bgithub.com%2Farvindr226%2Fphp-5.6-alpine?ref=badge_shield)


This Docker image has almost all php5.6 modules including the ffmpeg, imagemagick and gimp.

>Use the below docker-compose.yml file for php5.6.
<pre>
version: "2.0"
services:
  web:
    container_name: php5.6
    image: gotechnies/php-5.6-alpine
    ports:
       - "80:80"
       - "443:443"
    links:
       - db
       - phpmyadmin
    volumes:
      - ./html:/var/www/html
    restart: always
  db:
    image: mysql:5.6
    container_name: database
    ports:
      - 3306:3306
    environment:
      MYSQL_DATABASE: mysql_server
      MYSQL_USER: magento2
      MYSQL_PASSWORD: gotechnies
      MYSQL_ROOT_PASSWORD: gotechnies
    restart: always
  phpmyadmin:
    image: phpmyadmin/phpmyadmin
    container_name: phpmyadmin
    environment:
     - PMA_ARBITRARY=1
    restart: always
    links:
     - db
    ports:
     - 8080:80
    volumes:
     - /sessions
</pre>

> $ docker-compose up -d



## License
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Farvindr226%2Fphp-5.6-alpine.svg?type=large)](https://app.fossa.com/projects/git%2Bgithub.com%2Farvindr226%2Fphp-5.6-alpine?ref=badge_large)