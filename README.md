# docker-multi-project
How to config docker for multi project? this guideline will help you.
Reference: [laravel-docker-wsl2](https://github.com/tdkhoavn/laravel-docker-wsl2)

## Structure
```
  /docker/
    base.services/
      docker-compose.yml
      data/
  /project-name-01/
    docker-compose.yml
  /project-name-02/
    docker-compose.yml
```
`/docker/base.services/docker-compose.yml` contain the services: 
 - mysql
 - phpmyadmin
 - adminer
 - reverse-proxy
 - nodejs
You also can add more services into this file.

`/project-name-x/docker-compose.yml` contain the webserver of the project.

## Installation
Assume that you have successfully installed docker before.
### Create image of services:
```
cd /docker/base.services/
docker-compose up -d
```

### Create webserver of each container
```
cd /project-name-01/
docker-compose up -d

cd /project-name-02/
docker-compose up -d
```
Start container
```
docker container start projectname01
```
`Projectname01` is container name.

## Usesage
### Nodejs
```
cd app/projectname01/
```
Then you can use `npm` commands, like `npm run watch`.

### Webserver
```
cd app/
```
Then you can use the commands for your project, like `php artisan ...` (if you using the Laravel project).

### phpMyAdmin
[http://localhost:9090/](http://localhost:9090/)

### Adminer
[http://localhost:9091/](http://localhost:9091/)

## Something missing?

If you have any problems, [let me know](https://github.com/hocwebchuan/ReactMySQL-View-Insert-Update-Delete/issues).<br>
Thanks for using it!
