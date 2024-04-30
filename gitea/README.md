# Gitea

## Description
This `compose.yml` file will deploy a working installation of the [Gitea](https://about.gitea.com/) version control code hosting platform.

:warning: WARNING

In addition to the files in `secrets`, ensure you update the `.env` file as well with the password Gitea uses to connecto the the Database. This value will be the same as what is in `secrets/mysql_db_pw.txt`

## Docker Containers Created
This `compose.yml` file will create the following docker containers

| container | docker image | description |
| --------- | ------------ | ----------- |
|  | mysql:8 | MySQL based Database server |
| gitea | gitea/gitea:1.21.11 | Gitea code hosting Server |

## Secrets Used
The following secrets in the `secrets` directory will need to be configured before launching this docker compose file

| Secret | Description |
| ------ | ----------- |
| mysql_db_pw.txt | Password for the Database user that Gitea will use |
| mysql_root_pw.txt | Master Password for the mysql `root` user |

## Exposed Network Ports

| Port | Docker Container | Description |
| ---- | ---------------- | ----------- |
| 3000 | gitea | Used for accessing the Web UI |
| 222 | gitea | Used for SSH access to gitea repositories |

## Installation

1. Clone this directory down to your machine
2. Update the secret files in the `secrets` directory. 
3. Update `.env` with the value in the `secrets/mysql_db_pw` file. 
4. run `docker compose up -d`

