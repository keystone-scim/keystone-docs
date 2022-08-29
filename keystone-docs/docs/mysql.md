# MySQL Store

![Keystone MySQL](./assets/img/keysyone_mysql.png)

## Overview

You can configure Keystone to point to a [MySQL](https://dev.mysql.com/) server,
wherever it may reside. Keystone will attempt to create its tables and indeces upon startup
if they do not yet exist.  Please read further to learn how to configure Keystone
with a MySQL server.

## Prerequisites

You'll need to ensure the following criteria are met:

* **MySQL 5.7.8 or higher**: Keystone makes use of MySQL features available
  in MySQL version 5.7.8 or higher (e.g., `JSON` object type).  If you can, use the latest stable
  version of MySQL.
* **Permissions for workload user**: the user running the workload will have to own the database object Keystone is configured to
  run in.  Keystone will not try to create the database object.

## Example

The following YAML file and environment variables is a valid way to configure *Keystone* to point to
your MySQL database as its data store.

Create a file and call it `keystone_config.yaml`

```yaml
store:
  mysql:
    host: mysql.server.com
    port: 3306
    username: keystoneuser
    database: mysql
    ssl: require
```

Run the container, while bind-mounting the configuration file as a volume, along with
environment variables for secrets:

```shell
docker run -it \
  -p 5001:5001 \
  --mount type=bind,source="$(pwd)"/keystone_config.yaml,target=/etc/keystone_config.yaml
  -e AUTHENTICATION_SECRET="<extra secret bearer token>" \
  -e STORE_MYSQL_PASSWORD="<extra secret mysql password>" \
  -e CONFIG_PATH=/etc/keystone_config.yaml
  ghcr.io/keystone-scim/keystone:latest
```
