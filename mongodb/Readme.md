# MongoDB Docker Setup

This setup uses Docker to run a MongoDB container. Below is the `docker-compose.yml` configuration:

```yaml
version: "3.8"

services:
  mongo:
    image: mongo:latest
    restart: always
    container_name: mongo
    ports:
      - 27017:27017 # make sure we don't have another mongo container running on same port
    environment:
      MONGO_INITDB_ROOT_USERNAME: root
      MONGO_INITDB_ROOT_PASSWORD: root
    volumes:
      - ./db_data/:/data/db/
```

## Explanation

- **image**: Specifies the Docker image to use, in this case, the latest MongoDB image.
- **restart**: Always restart the container if it stops.
- **container_name**: Names the container `mongo`.
- **ports**: Maps port 27017 on the host to port 27017 on the container.
- **environment**: Sets the environment variables for the MongoDB root username and password.
- **volumes**: Mounts the `./db_data/` directory on the host to `/data/db/` in the container to persist data.

## Connection URL

To connect to this MongoDB instance, use the following URL:

```
mongodb://root:root@localhost:27017/
```

This URL includes the root username and password specified in the environment variables.
