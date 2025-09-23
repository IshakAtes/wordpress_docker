# WordPress Docker Setup

**Guide**:<br>
[Link to Pdf Checklist](https://github.com/IshakAtes/wordpress_docker/blob/988a9956ce0a28dd5155a18497beed856d5ea06d/Wordpress%20Checkliste.pdf)<br><br>

## Table of Contents
1. [About](#about)
2. [Quickstart](#quickstart)
3. [Usage](#usage)

## About
This repository contains a minimal WordPress + MySQL setup using Docker Compose.  
The purpose is to provide a reproducible, easy-to-use environment for running a personal WordPress blog.

## Quickstart
### Requirements
- Docker & Docker Compose

### Steps
1. Clone this repository  
```bash
git clone https://github.com/IshakAtes/wordpress_docker.git
cd wordpress-docker
```

2. Create a .env file in the project root:
``` env
MYSQL_DATABASE=wordpress
MYSQL_USER=wp_user
MYSQL_PASSWORD=wp_pass
MYSQL_ROOT_PASSWORD=root_pass

WORDPRESS_DB_HOST=db:3306
WORDPRESS_DB_NAME=wordpress
WORDPRESS_DB_USER=wp_user
WORDPRESS_DB_PASSWORD=wp_pass
```

3. Start the containers:
``` bash
docker compose up -d
```

4. Open `http://<IP_ADRESS>:8080` and complete the WordPress setup.


## Usage

**Persistency:**
- Data is stored in Docker volumes db_data and wordpress_data. Restarting or stopping containers will not remove data.

**Configuration:**
- Change environment variables in `.env` to customize database name, user, and passwords.
- To run WordPress on another port, change the `8080:80` mapping in `docker-compose.yaml`.

**Maintenance:**
- Stop services: `docker compose down`
- Restart services: `docker compose up -d`
- Remove all data (reset): `docker compose down -v`

**Security Notes**
- Do not commit your `.env` file with credentials.
- Use strong passwords.
- Run on a secure server (firewall, HTTPS via reverse proxy recommended).
