# Docker-Powered Database

This repository contains Docker configurations for setting up various databases. Each database has its own Docker Compose YAML file for easy setup and management.

## Databases

- MongoDB
- MySQL
- PostgreSQL
- Redis

## Setup Instructions

### MongoDB

1. Navigate to the MongoDB directory:
   ```sh
   cd mongodb
   ```
2. Start the MongoDB container:
   ```sh
   docker-compose -f mongodb-setup.yml up -d
   ```

### MySQL

1. Navigate to the MySQL directory:
   ```sh
   cd mysql
   ```
2. Start the MySQL container:
   ```sh
   docker-compose -f mysql-setup.yml up -d
   ```

### PostgreSQL

1. Navigate to the PostgreSQL directory:
   ```sh
   cd postgres
   ```
2. Start the PostgreSQL container:
   ```sh
   docker-compose -f postgres-setup.yml up -d
   ```

### Redis

1. Navigate to the Redis directory:
   ```sh
   cd redis
   ```
2. Start the Redis container:
   ```sh
   docker-compose -f redis-setup.yml up -d
   ```

## Stopping the Containers

To stop any running container, navigate to the respective directory and run:

```sh
docker-compose -f <file-name> down
```

Replace `<file-name>` with the appropriate YAML file name for the database you want to stop.

## Configuration Files

Each database has its own Docker Compose YAML file named as follows:

- MongoDB: `mongodb-setup.yml`
- MySQL: `mysql-setup.yml`
- PostgreSQL: `postgres-setup.yml`
- Redis: `redis-setup.yml`

Make sure to use the correct file name when starting the containers.
