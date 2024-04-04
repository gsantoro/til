---
title: Nodejs install package from source
draft: true
tags: 

---
# Nodejs install package from source
First you need to build the package from source with

```
npm run build
```

if package.json supports a script `build`

Install package from source with their dependencies first locally and then globally

```
npm install .
npm install -g .
```

List installed packages locally and globally

```
npm list
npm list -g
```

Clean cache

```
npm cache clean --force
```

If a file depends on an external package that is available on the local file system you can use

```
{
  "name": "test",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "dependencies": {
    "@elastic/synthetics": "file:/path"
  }
}
```