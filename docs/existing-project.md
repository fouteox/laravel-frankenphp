# Installing on an Existing Project

It's also possible to use Laravel Docker with existing projects!

First, clone this projet without .git :

    git clone --depth=1 https://github.com/fouteox/laravel-frankenphp.git && rm -rf laravel-frankenphp/.git

Then, copy the Docker-related files from the skeleton to your existing project:

    cp -Rp laravel-frankenphp/. my-existing-project/

Build the Docker images:

    docker compose build --no-cache --pull

Start the project!

    docker compose up -d

Browse [https://localhost](https://localhost), your Docker configuration is ready!

> [!NOTE]
> The worker mode of FrankenPHP is enabled by default in prod. To disabled it, add the env var FRANKENPHP_CONFIG as empty to the compose.prod.yaml file.
