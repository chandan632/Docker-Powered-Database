# Redis and Redis Commander Setup

This guide will help you set up Redis and Redis Commander using Docker Compose.

## Docker Compose Configuration

Here is the Docker Compose configuration to set up Redis and Redis Commander:

```yaml
version: "3.8"

services:
  redis:
    image: redis:latest
    restart: always
    container_name: redis
    ports:
      - "6379:6379"
    volumes:
      - ./redis_data:/data
    command: ["redis-server", "--appendonly", "yes"]

  redis-commander:
    image: rediscommander/redis-commander:latest
    restart: always
    container_name: redis-commander
    environment:
      REDIS_HOSTS: local:redis:6379
    ports:
      - "8081:8081"
    depends_on:
      - redis
```

## Running the Services

To start the services, run the following command in the directory containing the `docker-compose.yml` file:

```sh
docker-compose up -d
```

## Accessing Redis Commander

Once the services are up and running, you can access Redis Commander through the following URL:

```
http://localhost:8081
```

This will allow you to manage your Redis instance through a web interface.

## Stopping the Services

To stop the services, run:

```sh
docker-compose down
```

## Data Persistence

The Redis data is persisted in the `./redis_data` directory on your host machine. This ensures that your data is not lost when the container is stopped or removed.

## Additional Information

- Redis is configured to use append-only file persistence.
- Redis Commander is configured to connect to the Redis instance running on `redis:6379`.

Feel free to customize the configuration as needed for your environment.
