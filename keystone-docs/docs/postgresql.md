# PostgreSQL Store

## Overview

You can configure Keystone to point to a [PostgreSQL](https://www.postgresql.org/) server,
wherever it may reside. Keystone will attempt to create its database objects upon startup
if they do not yet exist.  Please ready further to understand how to configure Keystone
with a PostgreSQL server.

## Prerequisites

You'll need to ensure the following criteria are met:

* **PostgreSQL 10 or higher**: Keystone makes use of PostgreSQL features available
  in PostgreSQL version 10 or higher (e.g., `ILIKE` comparisons and the `CITEXT` extension).
* **The ability to install the [CITEXT extension](https://www.postgresql.org/docs/current/citext.html)**:
  Some managed database services (such as
  [Azure Database for PostgreSQL - Flexible Server](https://docs.microsoft.com/en-us/azure/postgresql/flexible-server/concepts-extensions))
  require adminsitrators to allow certain extensions explicitly.  Check that your PostgreSQL instance
  allows the creation of the `CITEXT` extension.
* **Permissions for workload user**: the user running the workload will have to own the schema it's configured to
  run in.  If the schema doesn't exist, Keystone will try to create a schema under that name.


## Configuration Reference

!!! info "YAML file or Environment Variables?"

    The short answer: **either or both**. You can populate some, all, or none of the configuration keys using environment
    variables. All configuration keys can be represented by an environment variable by
    the capitalizing the entire key name and replacing the nesting dot (`.`) annotation with
    an underscore (`_`).
    For example, `store.pg_username` can be populated with the
    `STORE_PG_USERNAME` environment variable in the container
    the API is running in.


| YAML Key            | Description                  | Env. Var.           | Default     |
| ------------------- | ---------------------------- | ------------------- | ----------- |
| `store.pg_host`     | PostgeSQL server's hostname  | `STORE_PG_HOST`     | `localhost` |
| `store.pg_port`     | Port to use                  | `STORE_PG_PORT`     | `5432`      |
| `store.pg_ssl_mode` | Connection SSL mode          | `STORE_PG_SSL_MODE` | `require`   |
| `store.pg_username` | Username for authentication  | `STORE_PG_USERNAME` | -           |
| `store.pg_password` | Password for authentication  | `STORE_PG_PASSWORD` | -           |
| `store.pg_database` | The PostgreSQL database name | `STORE_PG_DATABASE` | `postgers`  |
| `store.pg_schema`   | The PG username              | `STORE_PG_SCHEMA`   | `public`    |

