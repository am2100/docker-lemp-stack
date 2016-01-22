# Docker LEMP Stack
An example docker-compose build of a Linux, Nginx, MySQL and PHP stack.

Taken from: http://blog.osteel.me/posts/2015/12/18/from-vagrant-to-docker-how-to-use-docker-for-local-web-development.html?_tmc=p9YSlYM8PUi910_DgJBWHWy5TAOXitPRIcD-63k32ac&mkt_tok=3RkMMJWWfF9wsRonuqTMZKXonjHpfsX57e0oX66%2FlMI%2F0ER3fOvrPUfGjI4DTsJjI%2BSLDwEYGJlv6SgFQ7LMMaZq1rgMXBk%3D

## Install docker-compose as superuser
URL: https://github.com/docker/compose/releases

For version 1.5.2
```
sudo -i
curl -L https://github.com/docker/compose/releases/download/1.5.2/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
exit
```

## Verify installation was successful
```
docker-compose --version
> docker-compose version 1.5.2, build 7240ff3
```

## Install docker-machine as a superuser
URL: https://docs.docker.com/machine/install-machine/

`docker-machine` is installed in the tutorial as part of the Docker Toolbelt software that is used on Mac OSX. In the tutorial it is used to discover the IP address of a running `docker-compose` specified container, so that the nginx service can be verified as `up` via a browser.

On a Linux box setup, the IP address of the container can be looked up with the `docker inspect <containerId>` command. For that reason, it's not necessary in this instance to install the `docker-machine` binaries on a local setup.

```
sudo -i
curl -L https://github.com/docker/machine/releases/download/v0.5.3/docker-machine_linux-amd64 >/usr/local/bin/docker-machine
chmod +x /usr/local/bin/docker-machine
exit
```

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

