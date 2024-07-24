---
title: git Reset main to upstream
draft: true
tags:
  - git
---
# Git Reset main to upstream
If you push a commit by mistake to the main branch of a fork repo and you want to revert those commits you can run

```bash
GIT_PR_NUMBER=72
git fetch origin pull/${GIT_PR_NUMBER}/head:pr-${GIT_PR_NUMBER} && git checkout pr-${GIT_PR_NUMBER}
```

more info at [git reset main to upstream without pushing](https://stackoverflow.com/questions/29049650/github-fork-your-branch-is-5-commits-ahead-how-to-clean-this-without-pushing).