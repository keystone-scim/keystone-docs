# Configuring a Keystone Container

Read below to understand how you can configure a *Keystone* container
based on your needs.

## Before You Begin

### Choose How to Confiugre the Container

*Keystone* can be configured in one of two ways:

* **YAML File**: A YAML configuration file mounted as a volume onto the container.
  The path to your configuration YAML file needs to be specified in the `CONFIG_PATH`
  environment variable.
* **Environment Variables**: All of the configuration keys can be represented with
  environment variables.

You can configure Keystone with either of the two or with a combination of the two,
but it is recommended to *avoid* storing secrets in a YAML file. Instead, secrets should
be passed to the container using environment variables.

### Configuration Checklist

* **Choose your storage:**
  *Keystone* currently allows you to use one of the following storage layers:
    * [Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/introduction)
    * [PostgreSQL](https://www.postgresql.org) (version 10 or higher)
    * An in-memory store for **testing purposes only**.

* **Choose the token retrieval method:**
  *Keystone* currently allows you to specify that secret bearer token in two places:
      * In an [Azure Key Vault](https://azure.microsoft.com/en-us/services/key-vault/) secret.
      * In a configuration value (`AUTHENTICATION_SECRET` environment variable).

## Configuration Reference

| Key                                     | Description                                                                          | Default                |
| --------------------------------------- | ------------------------------------------------------------------------------------ | ---------------------- |
| `store.type`                            | Storage type. Supported values: `PostgreSQL`, `CosmosDB`, `InMemory`                 | `InMemory`             |
| `store.pg_host`                         | PostgeSQL server's hostname, if using a PostgeSQL store                              | `localhost`            |
| `store.pg_port`                         | Port to use, if using a PostgeSQL store                                              | `5432`                 |
| `store.pg_ssl_mode`                     | Connection SSL mode, if using a PostgeSQL store                                      | `require`              |
| `store.pg_username`                     | Username for authentication, if using a PostgeSQL store                              | -                      |
| `store.pg_password`                     | Password for authentication, if using a PostgeSQL store                              | -                      |
| `store.pg_database`                     | The PostgreSQL database name, if using a PostgeSQL store                             | `postgers`             |
| `store.pg_schema`                       | The PG schema, if using a PostgeSQL store                                            | `public`               |
| `store.tenant_id`                       | Azure Tenant ID, if using a Cosmos DB store with Client Secret Credentials auth.     | -                      |
| `store.client_id`                       | Azure Client ID, if using a Cosmos DB store with Client Secret Credentials auth.     | -                      |
| `store.secret`                          | Azure Client Secret, if using a Cosmos DB store with Client Secret Credentials auth. | -                      |
| `store.cosmos_account_uri`              | Cosmos Account URI, if using a Cosmos DB store                                       | -                      |
| `store.cosmos_account_key`              | Cosmos DB account key, if using a Cosmos DB store with Account Key auth.             | -                      |
| `store.cosmos_db_name`                  | Cosmos DB database name, if using a Cosmos DB store                                  | `scim_2_identity_pool` |
| `authentication.secret`                 | Plain secret bearer token                                                            | -                      |
| `authentication.akv.vault_name`         | AKV name, if bearer token is stored in AKV.                                          | -                      |
| `authentication.akv.secret_name`        | AKV secret name, if bearer token is stored in AKV.                                   | `scim-2-api-token`     |
| `authentication.akv.credentials_client` | Credentials client type, if bearer token is stored in AKV.                           | `default`              |
| `authentication.akv.force_create`       | Try to create an AKV secret on startup, if bearer token to be stored in AKV.         | `false`                |
