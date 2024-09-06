---
title: git Reset main to upstream
draft: true
tags:
  - git
---
# Git clean rebase
Every time I do a rebase of a feature branch that fell behind main, VisualStudio code complains that I should push N other commits that I didn't authored.

So the PR has lots of unrelated commits. To avoid this push with `--force-with-lease

```bash
git push --force-with-lease origin your-feature-branch-name
```

Use `--force-with-lease`: This is a safer option than `--force` as it ensures you don't accidentally overwrite someone else's work[git_rebase](https://docs.gitlab.com/ee/topics/git/git_rebase.html).