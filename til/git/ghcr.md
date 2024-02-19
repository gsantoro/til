---
title: Ghcr - Github cotainer registry
draft: true
tags: 

---
# Ghcr - Github container registry
1. build container

```bash
docker build -t <image_name>:<tag_version> .
```

1. tag container

```bash
docker tag <image_id> ghcr.io/<github_username>/<image_name>:<tag_version>
```

1. create Github personal token

More info at [Authenticating with a persoal access token (classic)](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry#authenticating-with-a-personal-access-token-classic)

1. docker login

```bash
export CR_PAT=<token>
echo $CR_PAT | docker login ghcr.io -u gsantoro --password-stdin
```

1. push container

```bash
docker push ghcr.io/<github_username>/<image_name>:<tag_version>
```

1. Check image in github under Packages.

You can link a container image with a Github container registry with the following Dockerfile label

```
org.opencontainers.image.source = "https://github.com/<github_username>/<github_repo>"
```

alternatively you can just push to the right repo URL