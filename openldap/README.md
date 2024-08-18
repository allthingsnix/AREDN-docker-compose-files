# OpenLDAP and phpLDAPadmin

## Description
This `compose.yml` file will deploy a working installation of [OpenLDAP](https://www.openldap.org/) directory services and [phpLDAPadmin](https://sourceforge.net/projects/phpldapadmin/) for directory management. 

## Docker Containers Created
This `compose.yml` file will create the following docker containers

| container | docker image | description |
| --------- | ------------ | ----------- |
| openldap | osixia/openldap | OpenLDAP directory services installation |
| phpldapadmin | osixia/phpldapadmin | phpLDAPadmin PHP frontend |

## Secrets Used
The following secrets in the `secrets` directory will need to be configured before launching this docker compose file

| Secret | Description |
| ------ | ----------- |
| ldap_admin_password.txt | Password for the 'admin' LDAP user account used to administer the directory. |
| ldap_config_password.txt | Password used to configure the directory. |
| ldap_readonly_password.txt | Password for the 'ro-user' LDAP user account. This account can only view the directory and cannot make any changes. |

## Exposed Network Ports

| Port | Docker Container | Description |
| ---- | ---------------- | ----------- |
| 389 | openldap | Used for accessing openldap directory over ldap:// |
| 8480 | phpldapadmin | Used for accessing the phpLDAPadmin web UI. `http://<address of your AREDN node>:8480` |

## Installation

1. Clone this directory down to your machine
2. Update the secret files in the `secrets` directory. 
3. run `docker compose up -d`
4. Open a web browser and navigate to `http://<address of your AREDN node>:8480`

