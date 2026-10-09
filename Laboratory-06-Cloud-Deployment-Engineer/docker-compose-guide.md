# Docker Compose Guide (Nextcloud + MariaDB)

> Purpose: help another engineer read and understand the `docker-compose.yml` used in this lab.

## File at a Glance

| Line / Block | Meaning |
|---|---|
| `version: '3'` | Compose file format version (newer Docker versions ignore it) |
| `services:` | The list of containers that make up the app |
| `database:` | Service name for the MariaDB container |
| `image: mariadb:10.6` | Use MariaDB version 10.6 from Docker Hub |
| `app:` | Service name for the Nextcloud container |
| `image: nextcloud` | Use the official Nextcloud image |
| `ports: - 8080:80` | Open port 8080 on the host and send it to port 80 in the container |
| `environment:` | Settings passed into the container as variables |

## Q1. What does the `services:` block do?

It is the heart of a Compose file. Everything under `services:` is a container that Compose should create and run. Here there are two:

- **`database`**: stores the data
- **`app`**: runs Nextcloud

For each service, Compose pulls the image, applies the settings, and starts the container. It also puts all services on one shared private network automatically, so you do not have to set up networking yourself.

## Q2. How did the app container find the database container?

The answer is the line `MYSQL_HOST=database`.

1. Compose builds one private network for the stack.
2. On that network, each service can be reached using its **service name** as a hostname.
3. The database service is named `database`, so Nextcloud just connects to the host called `database`.
4. Docker's internal DNS turns that name into the MariaDB container's current IP address.

This means the engineer never needs to look up or type an IP address. The user, password, and database name must also be the same on both sides (`MYSQL_USER`, `MYSQL_PASSWORD`, `MYSQL_DATABASE`), or the login will fail.

## Q3. `docker run` vs `docker-compose up -d`

**`docker run`**
- Starts a single container
- All options are typed into the command line each time
- Networking between containers must be arranged by hand
- Every container needs its own stop/remove command

**`docker-compose up -d`**
- Starts every service listed in the YAML file
- Options are saved in the file, so they can be reused and version-controlled
- Network is created automatically
- One command (`docker-compose down`) removes everything

The `-d` flag means *detached*: the containers run in the background and give the terminal back to you.

## Summary

`docker run` is like cooking one dish by hand; Docker Compose is like following a written recipe for a full meal. The recipe can be shared, repeated, and improved, which is the idea behind **Infrastructure as Code**.
