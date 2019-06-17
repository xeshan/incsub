## Overview

This repository aimed to dockerise WEB (nginx) and PHP (php-fpm) service. 

## Get it up and running

- [Install docker on your machine.][install-docker]

- [Install docker-compose on your machine.][install-docker-compose]

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
