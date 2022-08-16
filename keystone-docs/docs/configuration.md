# Configuring a Keystone Container

For full documentation visit [mkdocs.org](https://www.mkdocs.org).

## Before You Begin

Keystone can be configured in one of two ways:

* **YAML File**: A YAML configuration file mounted as a volume onto the container
* **Environment Variables**: All of the configuration keys can be represented with
  environment variables.



## Available Stores

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.

## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.
