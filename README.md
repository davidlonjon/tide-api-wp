# Tide API WordPress Server

## Description

This repo will provision a WordPress server which will use the [wp-tide-api](https://github.com/xwp/wp-tide-api) plugin to implement the Tide API.

## Dependencies

- Docker: [https://docs.docker.com/engine/installation/](https://docs.docker.com/engine/installation/)

## How to run locally

* Clone the repo:

```
$ git clone --recursive git@github.com:davidlonjon/tide-api-wp.git
```

* Create a new `.env` file from the `.env.dist` file and edit the settings:

```
WORDPRESS_DB_HOST=db
WORDPRESS_DB_NAME=tide
WORDPRESS_DB_USER=tide
WORDPRESS_DB_PASSWORD=tide
MYSQL_DATABASE=tide
MYSQL_USER=tide
MYSQL_PASSWORD=tide
MYSQL_ROOT_PASSWORD=root
NGINX_HOST=tide-api.dev

```

Launch the WordPres Tide API server using the docker compose command from the root of the repo:

```
$ docker-compose up -d
```

Then run

```
$ docker-compose exec workspace bash
```

to get into the workspace container and run:

```
$ cd /var/www/html/wp-content/plugins/wp-tide-api && composer install

$ exit
```

Now you should be able the WordPress site install at [http://tide-api.dev](http://tide-api.dev).

Follow the instructions to install WordPress (this will be only done one time).

Then go to the plugins menu and activate the `WP Tide API` plugin.

Please note that the Tide API endpoints will not work due to a bug with PATH_INFO and nginx configuration. To fix it temporarily do:

- Edit the config/nginx/tide-api.conf.template in the repo and comment the line: `fastcgi_param PATH_INFO $fastcgi_path_info;`
- Then from the root of the repo run: `docker-compose down nginx` and `docker-compose up -d nginx`

Now you should have a working Tide API running from [http://tide-api.dev](http://tide-api.dev).

## How to run on production

TBC


