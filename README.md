# Buildpacks Demo

Intended to demonstrate that Paketo's builder container can be used to build a Spring Boot application, without spinning up additional containers.

This mimicks the restrictions of a GitLab setup, where CI pipelines can be crafted by users that use predetermined containers, but within those containers, you're unable to spin up a new one on demand for security reasons (well known host machine compromises e.g. via Docker socket).

Tools such as Paketo's `pack` and other tools such as `testcontainers` are cases where this GitLab setup has issues.

Here we demonstrate that at least for running buildpacks (without the `pack` command), we do not need containers.

## Start

Everything has been put into docker-compose.yml.
Running these commands should result in a succesfully pushed container image to our local Docker registry, courtesy of the `creator` CLI command and the various buildpacks in Paketo's `builder` container image.

```
docker compose start
docker compose logs demo-buildpacks -f
```

After the build process has completed, we should be able to pull the docker container image from our local registry with:

```
docker pull localhost:5443/demo-buildpacks:latest
```
