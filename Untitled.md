---
title: docker-commands
draft: true
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