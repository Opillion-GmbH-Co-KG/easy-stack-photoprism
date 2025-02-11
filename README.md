# EASY STACK PHOTOPRISM

## Introduction
[Photoprism](https://github.com/photoprism/photoprism) is a great tool for organizing photo collections. This stack offers a simple Docker Compose setup for getting familiar with Photoprism, including a few sample images generated with DALL·E, a precompiled latest image, and easy configuration via environment variables.

This is not a full development stack, but it provides an opportunity to get familiar with Photoprism and can also be run persistently.

This is a simple Docker Compose setup with a few sample images generated using DALL·E. The stack uses a precompiled `latest` image of Photoprism and provides an easy way to control it via environment variables.

#### Caution! Caution! This stack is intended for development use only and is not configured for production. For production use, please refer to the "Easy-Stack-Prod" stack - comming soon.

## Important Notice

We strongly recommend changing all passwords in the `.env.dist` file. These are purely test data and should not be used even in development mode.

### How to Update Environment Variables

1. Create a `.env` file next to `.env.dist`:
   ```sh
   cp .env.dist .env
   ```
2. Open the `.env` file and update the relevant values.
3. The `.env` file will be automatically loaded if it exists and will override the corresponding environment variables.


## Installation and Starting the Application
To install and start the application, follow these steps:

### Prerequisites
- Docker and Docker Compose must be installed on the system.

#### Before you run this project, ensure the following are installed on your host system:

- Git
- Docker
- Docker Compose
- Make

#### Build this stack

Clone this Project

```sh
git clone git@github.com:Opillion-GmbH-Co-KG/easy-stack-photoprism.git

cd ./easy-stack-photoprism

 ```

To start and install this stack:

```sh
make start
 ```
or

```sh
make restart
```

#### The stack up and running:

![Alt text](.makefile/assets/stack.png?raw=true" "The stack")

#### add your host ip, localhost, to this example: http://0.0.0.0:2342/library/login
![Alt text](.makefile/assets/photoprism.png?raw=true" "Photoprism")
##### (easy-stack-main photoprism container)

### Docker Containers
The application consists of several Docker containers that provide various services and extend the functionality of the application. The main containers and their functions are described below:

1. **Nginx**
    - **Image:** [opillion/nginx](https://hub.docker.com/repository/docker/opillion/nginx)
    - **Description:** Nginx serves as a web server and reverse proxy, directing traffic to the appropriate backend and frontend containers.
    - **Ports (preconfigured):**
        - **External:**
            - 0.0.0.0:8098 -> 8082/tcp
            - 0.0.0.0:4444 -> 8443/tcp
    - **Name:** easy-stack-main-prod-nginx-1

2. **PHP-FPM**
    - **Image:** [opillion/php8](https://hub.docker.com/repository/docker/opillion/php8)
    - **Description:** This container executes the PHP scripts and communicates with the Nginx web server.
    - **Ports (preconfigured):**
        - **Internal:**
            - 9000/tcp
    - **Name:** easy-stack-main-prod-php-fpm-1

3. **MySQL**
    - **Image:** [opillion/mysql](https://hub.docker.com/repository/docker/opillion/mysql)
    - **Description:** MySQL serves as the relational database for the application.
    - **Ports (preconfigured):**
        - **External:**
            - 0.0.0.0:33065 -> 3305/tcp
        - **Internal:**
            - 3306/tcp
            - 33060/tcp
    - **Name:** easy-stack-main-prod-mysql-1

4. **Redis**
    - **Image:** [opillion/redis](https://hub.docker.com/repository/docker/opillion/redis)
    - **Description:** Redis is used as an in-memory data structure store.
    - **Ports (preconfigured):**
        - **Internal:**
            - 6379/tcp
            - 9121/tcp
    - **Name:** easy-stack-main-prod-redis-1

5. **MariaDB**
    - **Image:** [opillion/maria](https://hub.docker.com/repository/docker/opillion/maria)
    - **Description:** MariaDB serves as an additional relational database for the application.
    - **Ports (preconfigured):**
        - **External:**
            - 0.0.0.0:33067 -> 3306/tcp
    - **Name:** easy-stack-main-prod-maria-1

6. **Photoprism**
    - **Image:** [opillion/photoprism](https://hub.docker.com/repository/docker/opillion/photoprism)
    - **Description:** Photoprism is used for photo management and organization.
    - **Ports (preconfigured):**
        - **External:**
            - 0.0.0.0:2342 -> 2342/tcp
    - **Name:** easy-stack-main-prod-photoprism-1

## License Information for Used Containers

| Container      | License                                  | License Link                                                     |
|----------------|------------------------------------------|------------------------------------------------------------------|
| **MariaDB**    | GPL v2                                   | [GPL v2](https://www.gnu.org/licenses/old-licenses/gpl-2.0.html) |
| **Photoprism** | GNU Affero General Public License v3.0   | [AGPL v3.0](https://github.com/photoprism/photoprism)            |
| **Easy-Stack** | GPL-3.0                                  | [GPL-3.0](https://www.gnu.org/licenses/gpl-3.0.html)             |


