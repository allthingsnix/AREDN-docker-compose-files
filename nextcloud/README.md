# Nextcloud

## Description
This `compose.yml` file will deploy a working installation of the [Nextcloud](https://nextcloud.com/) self-hosted file storage and sync platform.

## Docker Containers Created
This `compose.yml` file will create the following docker containers

| container | docker image | description |
| --------- | ------------ | ----------- |
| nextcloud-mysql | mariadb:10.6 | MySQL based Database server |
| nextcloud | nextcloud | Nextcloud File Storage Server |

## Secrets Used
The following secrets in the `secrets` directory will need to be configured before launching this docker compose file

| Secret | Description |
| ------ | ----------- |
| mysql_db_pw.txt | Password for the Database user that Nextcloud will use |
| mysql_root_pw.txt | Master Password for the mysql `root` user |

## Exposed Network Ports

| Port | Docker Container | Description |
| ---- | ---------------- | ----------- |
| 8080 | nextcloud | Used for accessing the Web UI |

## Installation

1. Clone this directory down to your machine
2. Update the secret files in the `secrets` directory. 
3. run `docker compose up -d`

