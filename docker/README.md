## Overview

This repository aimed to dockerise WEB (nginx) and PHP (php-fpm) service. 

- *php* folder contains dockerfile for php-fpm container which is running on 9000 port.  This container also running Memcache on port 11211 and ImageMagick.  
- *web* folder contains dockerfile for Nginx which is running on 80 port and its based on openresty.  This folder also have configuration file.


## Get it up and running

- Clone this repository.

``` bash
$ git clone https://github.com/xeshan/incsub.git 
```

- Switch to the docker directory.

``` bash
$ cd incsub/docker/ 
```

- Start the stack.

``` bash
$ docker-compose up --build
```

if want to run complete structure as daemon (background process) then add `-d`

That's it! You have now local cluster running web and php services.


http://localhost  `will browse from Web container`
http://localhost/info.php  `will browse from PHP container`
