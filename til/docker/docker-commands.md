---
title: docker-commands
draft: false
tags:
  - docker
---
# Some useful docker commands
1. Search a Docker container by name and then return the output as JSON

```bash
docker ps -f "name=<container-name>" --format json
```

> [!info] replace `<container-name>` with the name of the container you are looking for


2. Return the name of a container as output

```bash
docker ps --format "{{.Names}}"
```

3. Build an image for a different architecture

```bash
docker buildx build --platform linux/amd64 -t <image_name> .
```