---
title: Change git origin url
draft: false
tags:
  - git
---
# Change git origin URL
When trying to push to a Git repo, I got the following error.

```
Fatal: could not read Username for 'https://github.com': Device not configured.
```

This error concerns that the repo was configured to use HTTP, as you can see

```
til on  main [!⇡] on ☁️
➜ git remote -v
origin	https://github.com/gsantoro/til.git (fetch)
origin	https://github.com/gsantoro/til.git (push)
```

Since I prefer to use SSH keys instead, you can solve the problem by changing the origin URL to use SSH keys instead.

```
git remote set-url origin git@github.com:gsantoro/til.git
git remote set-url --push origin git@github.com:gsantoro/til.git
```

as you can see at 

```
til on  main [!⇡] on ☁️
➜ git remote -v
origin	git@github.com:gsantoro/til.git (fetch)
origin	git@github.com:gsantoro/til.git (push)
```