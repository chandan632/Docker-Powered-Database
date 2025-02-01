# MongoDB Sharded Cluster Setup with Docker

This document provides a detailed overview of the `mongodb-setup.yml` file, which is used to set up a MongoDB sharded cluster using Docker Compose. The setup includes config servers, shard servers, a mongos router, and a Mongo Express UI for managing the MongoDB cluster.

## Services

### Config Server

The config server stores metadata and configuration settings for the sharded cluster.

- **Service Name:** `config1`
- **Image:** `mongo:latest`
- **Ports:** `27019:27019`
- **Volumes:** `./config1_data:/data/db`
- **Environment Variables:**
  - `MONGO_INITDB_ROOT_USERNAME: admin`
  - `MONGO_INITDB_ROOT_PASSWORD: secret`
- **Command:**
  - `mongod --configsvr --replSet configReplSet --bind_ip_all --auth`

### Shard Servers

Shard servers store the actual data in the sharded cluster. Each shard is a replica set.

- **Shard 1**
  - **Service Name:** `shard1`
  - **Image:** `mongo:latest`
  - **Ports:** `27018:27018`
  - **Volumes:** `./shard1_data:/data/db`
  - **Environment Variables:**
    - `MONGO_INITDB_ROOT_USERNAME: admin`
    - `MONGO_INITDB_ROOT_PASSWORD: secret`
  - **Command:**
    - `mongod --shardsvr --replSet shardReplSet --bind_ip_all --auth`
- **Shard 2**
  - **Service Name:** `shard2`
  - **Image:** `mongo:latest`
  - **Ports:** `27020:27020`
  - **Volumes:** `./shard2_data:/data/db`
  - **Environment Variables:**
    - `MONGO_INITDB_ROOT_USERNAME: admin`
    - `MONGO_INITDB_ROOT_PASSWORD: secret`
  - **Command:**
    - `mongod --shardsvr --replSet shardReplSet --bind_ip_all --auth`

### Mongos Router

The mongos router directs client requests to the appropriate shard.

- **Service Name:** `mongos`
- **Image:** `mongo:latest`
- **Ports:** `27017:27017`
- **Depends On:** `config1`, `shard1`, `shard2`
- **Command:**
  - `mongos --configdb configReplSet/config1:27019 --bind_ip_all`

### Mongo Express UI

Mongo Express provides a web-based interface for managing the MongoDB cluster.

- **Service Name:** `mongo-express`
- **Image:** `mongo-express:latest`
- **Ports:** `8081:8081`
- **Depends On:** `mongos`
- **Environment Variables:**
  - `ME_CONFIG_MONGODB_ADMINUSERNAME: admin`
  - `ME_CONFIG_MONGODB_ADMINPASSWORD: secret`
  - `ME_CONFIG_MONGODB_SERVER: mongos`
  - `ME_CONFIG_MONGODB_PORT: 27017`
  - `ME_CONFIG_MONGODB_SSL: false`

## Networks

- **Network Name:** `mongo-cluster`
- **Driver:** `bridge`

## Usage

1. **Start the Cluster:**

   ```sh
   docker-compose -f mongodb-setup.yml up -d
   ```

2. **Access Mongo Express UI:**
   Open your browser and navigate to `http://localhost:8081`.

3. **MongoDB Connection URL:**
   Use the following connection URL to connect to the MongoDB cluster:
   ```
   mongodb://admin:secret@localhost:27017
   ```

This setup ensures a robust and scalable MongoDB sharded cluster environment using Docker containers.
