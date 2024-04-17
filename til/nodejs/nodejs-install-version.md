---
title: nodejs-install-version
draft: true
tags: 

---
# nodejs-install-version

```bash
# install nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash

# needed to use nvm in the same shell
. /root/.bashrc

# install a new version of nodejs and switch to it if that's the only one installed
nvm install v18.19.1

# change the default version
nvm use v18.19.1

# list current version
nvm current

# list all available versions
nvm ls
```