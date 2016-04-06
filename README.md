# Dopecker

This is very usufull shell command library for the Docker container work.

## Requirements

* [Docker](https://github.com/docker/docker)
* [peco](https://github.com/peco/peco)

## Getting started

### Quick start
```
$ git clone https://github.com/ontheroadjp/dopecker.git
$ source dopecker/dopecker
```

### Add .bashrc or .bash_profile

```
if [ -f /path/to/dopecker/dopecker ]; then
  source /path/to/dopecker/dopecker
fi
```

## Usage

Just type command and hit return key. no options, no arguments.

## Commands

### get docker container information

```
$ DD			# show list containers
$ DDimages		# show list images
$ DDid			# show specific container's id
$ DDip			# show specific container's IP Address
$ DDvol			# show specific container's mounted volumes
$ DDenv			# show specific container's environment variables
$ DDhosts		# show specific container's hosts file
$ DDps			# execute docker ps
$ DDpsa			# execute docker ps -a
$ DDi			# execute docker images
$ DDstats		# execute docker stats
$ DDtop			# execute docker top
$ DDlogs		# execute docker logs
$ DDlogsf		# execute docker logs -f
$ DDhistory		# execute docker history
$ DDinspect		# execute docker inspect
```

### control docker container

```
$ DDstart		# start specific container
$ DDstop		# stop specific container
$ DDrm			# remove specific container
$ DDrmi			# remove specific image
$ DDstopa		# stop all of running container
$ DDnone		# remove <none> images
$ DDreset		# stop and remove all of the container
```

### connect into docker container

```
$ DDbash		# connect into specific container with bash command
$ Ddmysql		# connect into specific container with mysql command
```

## Usage examples

Example) Using DD command which shows list of containers

1. Type command.

	```
	$ DD
	```

2. Then, show list containers like this.

	```
	--------------------------------
	<RUNNING>
	1: c40d6be871ff      nutsp/php:5.6-apache     toybox_www.starton.jp-php_1
	2: ea890b60fc08      mariadb                  toybox_www.starton.jp-php-db_1
	3: 3abb0a3ea952      wordpress                toybox_wordpress.docker-toybox.com-wordpress_1
	4: c5d23808608f      mariadb                  toybox_wordpress.docker-toybox.com-wordpress-db_1
	5: 3b57f305d320      jwilder/nginx-proxy      toybox_proxy_1
	--------------------------------
	<STOPPED>
	1: 0e1bc8616510      wordpress                toybox_blog.docker-toybox.com-wordpress_1
	2: 60e31d8ec558      mariadb                  toybox_blog.docker-toybox.com-wordpress-db_1
	```

Example) Using Ddip command which shows IP Address of specific container

1. Type command.

	```
	$ DDip
	```

2. Then, open peco with running containers

	```
	QUERY>                                                                                    IgnoreCase [1/1]
	c40d6be871ff        nutsp/php:5.6-apache   "/entrypoint.sh apac   15 hours ago        Up 15 hours         
	ea890b60fc08        mariadb                "/docker-entrypoint.   15 hours ago        Up 15 hours
	3abb0a3ea952        wordpress              "/entrypoint.sh apac   22 hours ago        Up 22 hours
	c5d23808608f        mariadb                "/docker-entrypoint.   22 hours ago        Up 22 hours
	3b57f305d320        jwilder/nginx-proxy    "/app/docker-entrypo   22 hours ago        Up 22 hours
	```

3. select container 
4. Finally, show IP Address your selected container

	```
	172.17.1.104
	```

Example) Using command in others

You can also use several commands in shell script.  

```
$ docker run -d -e PMA_HOST=$(DDip) -p 8080:80 phpmyadmin/phpmyadmin
```

This one is going to up phpMyAdmin container that is connected to specific container. You can access it ``http://xxx.xxx.xxx.xxx:8080``.


