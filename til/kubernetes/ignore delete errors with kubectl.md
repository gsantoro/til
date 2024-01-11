---
title: ignore errors when deleting kubernetes resources that don't exists
tags:
  - kubernetes
---
# Ignore errors when deleting Kubernetes resources that don't exists
When trying to delete a Kubernetes resource that don't exists, it fails with error

```
Error from server (NotFound): error when deleting "manifest.yml": <resource type> "<resource name>" not found
```

> [!warn] to notice that `<resource type>` and `<resource name>` are placeholders in the previous error


The solution is to ignore the error with the command

```shell
kubectl delete --ignore-not-found=true -f manifest.yml
```