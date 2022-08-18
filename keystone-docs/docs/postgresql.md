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
