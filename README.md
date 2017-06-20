![docker_logo_wordpress_installation_github](https://user-images.githubusercontent.com/26068468/27344127-8f2f4a96-55e5-11e7-9b29-aa4c860e046b.jpg)


Docker setup of local Wordpress, docker will handle the installation of all the services necessary for a Wordpress installation in its own containers therefore wont be necessary to install this services in the local machine.

<br />

## Description
The Docker configuration sets up 4 images:
  - docker_cron
  - docker_wordpress
  - redis
  - mysql
  - php

And after starts the containers to run them:
  - docker_cron_1
  - docker_wordpress_1
  - docker_mysql_1
  - docker_redis_1

<br />
<br />

## 0) Requirements: Docker / Node (Optional) / Npm (Optional) Installation

Install Docker and Docker-compose:

  - Docker. https://docs.docker.com/engine/installation/

  - Docker-compose.https://docs.docker.com/compose/install/

    Install Node.js & Npm (Optional):

  - https://nodejs.org/en/download/package-manager/


<br />
<br />

## 1) WP-dockerized use
**Build and run the image:**<br />

Clone the github WP-dockerized repository in your computer.

  git clone https://github.com/ericgraficode/WP-dockerized.git

From the GIT project folder execute these commands.

This command runs the scripts from the ./dockerfile:
```
docker-compose build
```

After build is ended...

This command runs ./docker-compose.yml config file.
```

docker-compose up
```
Wordpress is ready! reachable through 172.0.01:80.

*Wordpress: last version of wordpress is being included directly in the project. 

<br />

**1.A) Connect your hosts**<br />

At this point you will have all the containers running, Wordpress should be working with a default empty database called wp_database and should be accessible through 172.0.01:80, although in a development environment ideally you will be working with a Url that will resemble the production one, for that just edit your host file and point your local IP to the desired URL.

Wordpress should be working now and should be accessible through your browser in the specified url "http://exampleurl" Url.
Follow the steps Wordpress indicates you and install it. After log in "http://exampleurl/wp-admin".

<br />

**1.B) Configure the database**<br />

Now your Wordpress is fully running and accessible, you can edit your database. This repo comes with two Npm useful commands to populate and dump the database that is running inside the container that host mysql:

- This command will copy the content of the database located in the folder database into the database located inside the mysql container docker_mysql_1.
  ```
  Npm run populate
  ```

- This command will make a copy of the database located inside the mysql container docker_mysql_1 into the folder "database" located in the root of WP-dockerized.
  ```
  Npm run dump
  ```

<br />
<br />

## Reference & tips

**Important References:**

This repository has being build following the articles from Tomaž Zaman https://codeable.io/author/tom/.
<br/>
<br/>
This repository is intended to an efficient way to build multiple Wordpress local CMS, in a fast and reliable manner.
<br/>
<br/>
All contributions are welcome :heart:.

**Useful commands:**
- Console command to get container IP:

  ```docker inspect  docker_wordpress_1```

- Stops all the running containers:

  `docker stop $(docker ps -a -q)`

- Erase all the running containers:

  `docker rm $(docker ps -a -q)`

- Erase all the images:

  `docker rmi $(docker images -q)`

- Force erase all the images:

  `docker rmi --force $(docker images -q)`
