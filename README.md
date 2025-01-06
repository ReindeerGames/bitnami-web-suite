# Bitnami Web Suite with Docker Compose

This repository contains a `docker-compose.yml` file for deploying a full web suite using Bitnami's Docker images. The setup includes several services that are commonly used for web applications:

- **MariaDB databases** for various applications
- **WordPress** for website management
- **phpBB** for forum management
- **OSClass** for classifieds management

## Services

1. **MariaDB (for WordPress, phpBB, OSClass, and Store)**
   - Four separate MariaDB instances to manage databases for each application.
   - The MariaDB containers are configured with the required environment variables to set up the databases.

2. **WordPress (Site and Store)**
   - Two WordPress instances: one for a site and another for an e-commerce store.
   - Each WordPress instance connects to a separate MariaDB instance for database management.

3. **phpBB**
   - A forum application that connects to a separate MariaDB instance.

4. **OSClass**
   - A classifieds application that also connects to a separate MariaDB instance.

## Prerequisites

Before using this setup, make sure you have the following installed:

- **Docker**: Docker must be installed and running on your machine. [Install Docker](https://www.docker.com/get-started).
- **Docker Compose**: Docker Compose is required to define and run multi-container Docker applications. [Install Docker Compose](https://docs.docker.com/compose/install/).
- **Git**: Git is required to clone repositories and manage source code. [Install Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

## How to Use

### 1. Clone the Repository

Clone this repository to your local machine:

```bash
git clone https://github.com/ReindeerGames/bitnami-web-suite.git
cd bitnami-web-suite
```

### Configure the `.env` File

The `.env` file is used to configure environment variables that define database settings, application credentials, and other essential configurations for the Docker containers.

Create a `.env` file in the root of the repository with the following variables:

```bash
ADMIN_EMAIL=example@example.com
ADMIN_USER=admin
ADMIN_PASSWORD=secureadminpassword
DATABASE_PASSWORD=securedbpassword
DATABASE_ROOT_PASSWORD=securedbrootpassword
```
Next we run the command to launch the compose file:

```bash
docker compose up -d
```

# Monitoring the Progress of Docker Compose Stack

Once you've launched a stack using `docker-compose up -d`, you can check the progress of the installation or monitor the status of your services in several ways. Below are methods to check the progress.

## 1. Check the Logs for Specific Services

To see the installation or startup progress for a specific service, you can check its logs.

#### Command:
```bash
docker-compose logs <service-name>
```

Thanks for reading and feel free to reach out with any questions or comments. 
