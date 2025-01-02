Bitnami Web Suite with Docker Compose
This repository contains a docker-compose.yml file for deploying a full web suite using Bitnami's Docker images. The setup includes several services that are commonly used for web applications:

MariaDB databases for various applications
WordPress for website management
phpBB for forum management
OSClass for classifieds management
Services
MariaDB (for WordPress, phpBB, OSClass, and Store)

Four separate MariaDB instances to manage databases for each application.
The MariaDB containers are configured with the required environment variables to set up the databases.
WordPress (Site and Store)

Two WordPress instances: one for a site and another for an e-commerce store.
Each WordPress instance connects to a separate MariaDB instance for database management.
phpBB

A forum application that connects to a separate MariaDB instance.
OSClass

A classifieds application that also connects to a separate MariaDB instance.
Prerequisites
Before using this setup, make sure you have the following installed:

Docker: Docker must be installed and running on your machine. Install Docker.
Docker Compose: Docker Compose is required to define and run multi-container Docker applications. Install Docker Compose.
How to Use
Clone the Repository

Clone this repository to your local machine:

bash
Copy code
git clone https://github.com/ReindeerGames/bitnami-web-suite.git
cd bitnami-web-suite
Configure Environment Variables

The .env file is used to configure sensitive environment variables like passwords and usernames. Ensure that you modify the .env file with your own values.

Here's an example .env file:

dotenv
Copy code
MARIADB_ROOT_USER=root
MARIADB_ROOT_PASSWORD=password
MARIADB_USER=bitnami
MARIADB_PASSWORD=password

WORDPRESS_SITE_DB_NAME=wordpress_site
WORDPRESS_STORE_DB_NAME=wordpress_store
PHPBB_DB_NAME=shtf_phpbb
OSCLASS_DB_NAME=shtf_osclass

USERNAME=username
PASSWORD=password
Important: Make sure you replace the placeholders (password, username, etc.) with your own secure values.

Start the Containers

With Docker Compose, you can easily start all the services defined in the docker-compose.yml file:

bash
Copy code
docker-compose up -d
The -d flag runs the containers in the background.

Access the Applications

Once the containers are running, you can access each service through your web browser:

WordPress Site: http://localhost:8080
WordPress Store: http://localhost:8081
phpBB: http://localhost:8082
OSClass: http://localhost:8083
Use the credentials defined in the .env file for logging in (for example, username and password).

Stop the Containers

To stop the containers, you can run:

bash
Copy code
docker-compose down
This will stop and remove all the containers.

View Logs (Optional)

If you want to view logs for a specific container, you can use the docker-compose logs command:

bash
Copy code
docker-compose logs <container_name>
Example:

bash
Copy code
docker-compose logs wordpress_site
Configuration
You can modify the docker-compose.yml to suit your specific needs. For instance, you can add additional services, change ports, or adjust database settings.

The docker-compose.yml defines the services for WordPress, phpBB, and OSClass, along with their corresponding MariaDB database instances.
Volumes are defined to persist the data of the databases and websites even if the containers are stopped or removed.
Environment variables in the .env file allow you to easily manage the configuration of each container.
Troubleshooting
Permissions: Ensure that the folders (e.g., /home/shtf/mysql_site, /home/shtf/wordpress) on your host machine are accessible and have the correct permissions.
Ports: If you encounter issues with port conflicts, you can modify the ports in the docker-compose.yml file.
License
This project is licensed under the MIT License - see the LICENSE file for details.

This README should guide you through using the Bitnami Web Suite setup with Docker Compose. Let me know if you need more information!