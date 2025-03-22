# Redis and RedisInsight - Docker Compose Setup

## Overview
This Docker Compose setup includes:
- **Redis**: An in-memory data store used as a database, cache, and message broker.
- **RedisInsight**: A visualization tool to manage and monitor Redis databases.

## Prerequisites
Ensure you have the following installed on your system:
- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Setup and Usage

### 1. Clone the Repository
```sh
git clone <your-repository-url>
cd <your-repository-folder>
```

### 2. Start the Containers
Run the following command to start Redis and RedisInsight:
```sh
docker compose up -d
```
This will:
- Start the Redis container on **port 6379**
- Start the RedisInsight container on **port 8001**

### 3. Verify Running Containers
Check if the containers are running:
```sh
docker ps
```

### 4. Access RedisInsight
Open a browser and go to:
```
http://localhost:8001
```
Connect to Redis using **host: localhost** and **port: 6379**.

## Stopping the Containers
To stop the containers, run:
```sh
docker compose down
```

## Removing Containers and Volumes
To remove all associated containers and volumes:
```sh
docker compose down -v
```

## Persistent Storage
- **Redis data** is stored in the `redis-volume-data` volume.
- **RedisInsight data** is stored in the `redisinsight-data` volume.

## Troubleshooting
### Check Logs
If Redis or RedisInsight is not running properly, check the logs:
```sh
docker logs redis
```
```sh
docker logs redisinsight
```

### Restart Containers
```sh
docker compose restart
```

## License
This project is open-source and available for use under the [MIT License](LICENSE).

---
Enjoy using Redis with Docker! 🚀

