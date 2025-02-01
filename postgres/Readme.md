# PostgreSQL and pgAdmin Setup

This setup uses Docker to run PostgreSQL and pgAdmin. Below are the steps to get started.

## Docker Compose Configuration

```yaml
version: "3.8"

services:
  postgres:
    image: postgres:latest
    restart: always
    container_name: postgres
    environment:
      POSTGRES_PASSWORD: root
      POSTGRES_DB: mydb
      POSTGRES_USER: user
    ports:
      - "5432:5432"
    volumes:
      - ./postgres_data:/var/lib/postgresql/data

  pgadmin:
    image: dpage/pgadmin4:latest
    restart: always
    container_name: pgadmin
    environment:
      PGADMIN_DEFAULT_EMAIL: admin@admin.com
      PGADMIN_DEFAULT_PASSWORD: admin
    ports:
      - "8082:80"
    depends_on:
      - postgres
```

## Connection Details

### PostgreSQL

- **Host:** localhost
- **Port:** 5432
- **Database:** mydb
- **Username:** user
- **Password:** root

**Connection URL:**

```
postgresql://user:root@localhost:5432/mydb
```

### pgAdmin

- **URL:** http://localhost:8082
- **Email:** admin@admin.com
- **Password:** admin

## Instructions

1. Save the above Docker Compose configuration to a file named `docker-compose.yml`.
2. Run `docker-compose up -d` to start the services.
3. Access pgAdmin at [http://localhost:8082](http://localhost:8082) and log in with the provided email and password.
4. Add a new server in pgAdmin with the PostgreSQL connection details.

Enjoy your PostgreSQL and pgAdmin setup!
