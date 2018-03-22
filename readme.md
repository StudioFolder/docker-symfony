#Contributing Guidelines
### Frontend
To work on css and template go to the docker folder, start containers and access the website on 
localhost:8081

#### Start the containers in detached mode
`docker-compose up -d`

If you don't know what it means read here:
https://docs.docker.com/engine/reference/run/#detached-vs-foreground

#### To run composer or symfony php/bin commands
Php and composer are running inside the Docker container.
Verify containers are up and running with `docker-compose ps`.

Output should look like this:

```
     Name                   Command              State           Ports         
-------------------------------------------------------------------------------
docker_nginx_1   nginx -g daemon off;            Up      0.0.0.0:8081->80/tcp  
docker_php_1     docker-php-entrypoint php-fpm   Up      0.0.0.0:9002->9000/tcp
```

The name of the php service container is just php so:

`docker-compose exec php composer update`

or

`docker-compose exec php php bin/console debug:router`

#### Encore package manager

The php container comes with node npm and yarn installed.
You can verify which versions with

`docker-compose exec php node -v` 

You can follow instructions here to install encore: https://symfony
.com/doc/current/frontend/encore/installation.html
