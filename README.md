# Searx

![https://hub.docker.com/r/angristan/searx/](https://img.shields.io/microbadger/image-size/angristan/searx.svg?maxAge=3600&style=flat-square) ![https://hub.docker.com/r/angristan/searx/](https://img.shields.io/microbadger/layers/angristan/searx.svg?maxAge=3600&style=flat-square) ![https://hub.docker.com/r/angristan/searx/](https://img.shields.io/docker/pulls/angristan/searx.svg?maxAge=3600&style=flat-square) ![https://hub.docker.com/r/angristan/searx/](https://img.shields.io/docker/stars/angristan/searx.svg?maxAge=3600&style=flat-square)

![Searx](https://i.goopics.net/ls.png)

Based on [wonderfall/searx](https://github.com/Wonderfall/dockerfiles/tree/master/searx).

This image is automatically built by [GitLab CI](https://gitlab.com/angristan/docker-searx/pipelines) and pushed to the [Docker Hub](https://hub.docker.com/r/angristan/searx/).

**I won't update this image anymore. Feel free to fork the repo.**

## What is searx?

Searx is an open-source, privacy-respecting, hackable metasearch engine written in Python.

## Features

- Based on Alpine Linux.
- Latest code from [asciimoo/searx](https://github.com/asciimoo/searx)
- A unique secret key is generated when booting the first time.
- Ran as an unprivileged user (see `UID` and `GID`)

## Build-time variables

- **`SEARX_VER`**: Searx version (`0.15.0`)

## Environment variables

- **`IMAGE_PROXY`**: enables images proxying *(default: False)*
- **`BASE_URL`**: http://domain.tld *(default: False)*
- **`GID`**: group id *(default: `4242`)*
- **`UID`**: user id *(default: `4242`)*

## Usage

```sh
docker run -d \
  --name searx \
  -p 80:8888 \
  -e IMAGE_PROXY=true \
  -e BASE_URL=https://searx.domain.tld \
  -e UID=4242 \
  -e GID=4242 \
  angristan/searx:0.15
```

A `docker-compose.yml` example:

```yml
version: '2.3'

services:
  searx:
    container_name: searx
    image: angristan/searx:0.15
    restart: always
    ports:
      - "80:8888"
    environment:
      - IMAGE_PROXY=true
      - BASE_URL=https://searx.domain.tld
      - UID=4242
      - GID=4242
```
