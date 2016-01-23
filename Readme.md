# Docker LEMP Stack
An example docker-compose build of a Linux, Nginx, MySQL and PHP stack.

See [From Vagrant to Docker]( http://blog.osteel.me/posts/2015/12/18/from-vagrant-to-docker-how-to-use-docker-for-local-web-development.html?_tmc=p9YSlYM8PUi910_DgJBWHWy5TAOXitPRIcD-63k32ac&mkt_tok=3RkMMJWWfF9wsRonuqTMZKXonjHpfsX57e0oX66%2FlMI%2F0ER3fOvrPUfGjI4DTsJjI%2BSLDwEYGJlv6SgFQ7LMMaZq1rgMXBk%3D) article.

## Installation instructions
Links to installation instructions for Ubuntu (and other distributions / OS's) can be found on the [wiki](https://github.com/am2100/docker-lemp-stack/wiki).

## Stack description
Docker Compose allows you to describe your stack specifying the different containers that will compose it through a YAML config file. As the recommended practice is to have one process per container, we will separate things as follows:

1. a container for Nginx
1. a container for PHP-FPM
1. a container for MySQL
1. a container for phpMyAdmin
1. a container to make MySQL data persistent
1. a container for the application code

## Create docker-compose.yml
In the root directory
```yaml

