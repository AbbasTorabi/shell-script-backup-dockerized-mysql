# shell scipt to get backup dockerized mysql
This script connect to your mysql and get databases list, then exclude mysql default databases and get backup the rest of databases.

## Requirements
- docker [install docker](https://docs.docker.com/get-docker/)
- docker compose [install docker compose](https://docs.docker.com/compose/install/)
- Make sure that you have a Python entry in your PATH! Windows requires an environmental variable to be set at `My Computer ‣ Properties ‣ Advanced ‣ Environment Variables`. There's a few Stack Overflow questions about this.

## Config Mysql
### Config your mysql step by step:
- Docker compose:
```
version: '3'
services:
  mysql-dockerized:
    build:
      context: .
      dockerfile: Dockerfile
    container_name: mysql-dockerized-container
    restart: always
    ports:
      - '3306:3306'
    environment:
      - MYSQL_ROOT_PASSWORD=mysql_seure_password
    volumes:
      - './app:/usr/app'
```

- Dockerfile:
```
FROM mysql:latest
RUN touch config.cnf
COPY ./config.cnf config.cnf
```
- Using multiple flags is fine, but avoid using both `-s` & `-g` as this will duplicate your results.
- There are some script variables used to control the time format, wait time between tests and the results filename. Find them here:
```
currentTime
waitTime
resultsFile
```
- The wait time is in seconds.
