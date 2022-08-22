# MongoDB Store

![Keystone Mongo](./assets/img/keystone_mongo.png)

## Overview

You can configure Keystone to point to a [MongoDB](https://www.mongodb.com/docs/) instance,
wherever it may reside. Keystone will attempt to create its MongoDB database and collections upon startup
if they do not yet exist.  Please read further to learn how to configure Keystone
with a MongoDB store.

## Prerequisites

You'll need to ensure the following criteria are met:

* **MongoDB 3.6 or higher**: *Keystone* makes use of MongoDB features available
  in MongoDB version 3.6 or higher (e.g., collations for case-insensitive comparison, lookups, etc.).
* **Permissions for workload user**: the user running the workload will have to have sufficient permissions
  to create a database and collections in the MongoDB instance.

## Example

The following YAML file and environment variables is a valid way to configure *Keystone* to point to
your MongoDB instance as its data store.

Create a file and call it `keystone_config.yaml`

```yaml
store:
  mongo:
    host: my.mongodb.server.com
    port: 27017
    username: keystoneapiuser
    database: scim2Db
    tls: true
```

Run the container, while bind-mounting the configuration file as a volume, along with
environment variables for secrets:

```shell
docker run -it \
  -p 5001:5001 \
  --mount type=bind,source="$(pwd)"/keystone_config.yaml,target=/etc/keystone_config.yaml
  -e AUTHENTICATION_SECRET="<extra secret bearer token>" \
  -e STORE_MONGO_PASSWORD="<extra secret mongo password>" \
  -e CONFIG_PATH=/etc/keystone_config.yaml
  ghcr.io/keystone-scim/keystone:latest
```

Alternatively, you can configure *Keystone* with a MongoDB DSN.  Notice that the this example
skips the YAML configuration file altogether:

```shell
DSN="mongodb://user:<mongosecret>@mongohost1,mongohost2:27017/?tls=true&replicaSet=myReplicaSet"
docker run -it \
  -p 5001:5001 \
  -e AUTHENTICATION_SECRET="<extra secret bearer token>" \
  -e STORE_MONGO_DSN=${DSN} \
  ghcr.io/keystone-scim/keystone:latest
```
