---
title: obsidian-sync
tags:
  - obsidian
  - backup
---
# Sync local repos to GitHub
A simple bash script called `obsidian-sync.sh` that synchronise some repos to GitHub

```bash
#!/bin/bash

# make the script exit immediately if a command returns a non-zero exit status
set -e

# list of Obsidian vaults we want to sync
vault_basepath="/Users/`whoami`/vaults"

for vault in `ls ${vault_basepath}`
do
    echo "---------------------------------"

    echo "Walking into the vault: ${vault}"

    # walk into the vault directory
    cd ${vault_basepath}/${vault}

    # TODO: check this is a Git repository
    #

    # set git options for this repository only
    git config user.name "Automated"
    git config user.email "actions@users.noreply.github.com"

    # add everything changed to the stage
    git add -A .

    # commit everything changed
    timestamp=$(date -u)
    git commit -m "Latest data: ${timestamp}" || continue

    # push the commit to the remote repo
    git push

    echo "---------------------------------"
done
```

Assumptions:
- all repos have to be under `~/vaults`
- anything under that path is expected to be a git repo
- ssh keys to push to Git are already configured for the local user
- you need to provide execution permission with `chmod a+x obsidian-sync.sh`

How to configure this script to run on a schedule. Run the command

```
sudo crontab -e <username>
```

to create a crontab config for a user

```
0 * * * * ~/bin/obsidian-sync.sh >/tmp/obsidian-sync.log 2>&1
```

- [ ] Logs for that script will be store ad `/tmp/obsidian-sync.log`