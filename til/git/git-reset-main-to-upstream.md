---
title: git Reset main to upstream
draft: true
tags:
  - git
---
# Git Reset main to upstream
If you push a commit by mistake to the main branch of a fork repo and you want to revert those commits you can run

```bash
git fetch upstream
git diff upstream/main..main
git reset --hard upstream/main
git push origin main --force
```

more info at [git reset main to upstream without pushing](https://stackoverflow.com/questions/29049650/github-fork-your-branch-is-5-commits-ahead-how-to-clean-this-without-pushing).