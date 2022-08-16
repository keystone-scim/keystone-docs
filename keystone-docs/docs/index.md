# Getting Started

Welcome to the official *Keystone* Documentation site.

!!! warning "Pre-release"

    *Keystone* is in a pre-release stage, and as such, its documentation
    is missing everything you need to know before you can configure a
    *Keystone* container. Stay tuned for its first major release (0.1.0)!

## What's Keystone?

*Keystone* is a fully containerized lightweight SCIM 2.0 API implementation.
Whether you're using one of the prominent cloud identity managers such as
Azure Active Directory, Okta, Auth0, etc., or another identity provider that supports
automatic provisioning with SCIM 2.0, you can use *Keystone* to quickly store
the state of directory in a [data store](#supported-data-store).

## Supported Data Store

As *Keystone* is an entirely stateless workload, it expects you to bring your own
storage layer, and it'll take care of the nitty-gritty details, such as schema
and tables creation.  All you have to do is provision a supported data store in
a network location that your *Keystone* container can reach.

*Keystone* currently supports the following data stores:

  * [Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/introduction)
  * [PostgreSQL](https://www.postgresql.org) (version 10 or higher)
  * An in-memory for **testing purposes only**.
