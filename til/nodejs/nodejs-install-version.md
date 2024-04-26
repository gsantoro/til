---
title: nodejs-install-version
draft: false
tags:
---
# nodejs-install-version
How to install a custom version of nodejs with [Node version manager](https://github.com/nvm-sh/nvm)

```bash
# install nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash


# needed to use nvm in the same shell
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"

# install a new version of nodejs and switch to it 
# if it is the only version installed
nvm install v18.19.1
```

Some extra commands

```bash
# change the default version
nvm use v18.19.1

# List the current version
nvm current

# List all available versions
nvm ls
```