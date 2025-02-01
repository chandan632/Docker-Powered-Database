# Docker-Powered MySQL Database

This project sets up a MySQL database and phpMyAdmin using Docker.

## Services

### MySQL

- **Image**: `mysql:latest`
- **Container Name**: `mysql`
- **Environment Variables**:
  - `MYSQL_ROOT_PASSWORD`: root
  - `MYSQL_DATABASE`: mydb
  - `MYSQL_USER`: user
  - `MYSQL_PASSWORD`: root
- **Ports**: `3306:3306`
- **Volumes**: `./mysql_data:/var/lib/mysql`

### phpMyAdmin

- **Image**: `phpmyadmin/phpmyadmin:latest`
- **Container Name**: `phpmyadmin`
- **Environment Variables**:
  - `PMA_HOST`: mysql
  - `PMA_USER`: root
  - `PMA_PASSWORD`: root
- **Ports**: `8080:80`
- **Depends On**: `mysql`

## Connection URL

- **MySQL**: `mysql://user:root@localhost:3306/mydb`
- **phpMyAdmin**: `http://localhost:8080`

## Usage

1. Ensure Docker is installed and running on your machine.
2. Save the provided `docker-compose.yml` content to a file.
3. Run `docker-compose up -d` to start the services.
4. Access phpMyAdmin at `http://localhost:8080` and use the MySQL credentials to manage your database.
