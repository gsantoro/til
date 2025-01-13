# Git - safe rebase
I find it very confusing how Git rebase work.

If you have just a branch and no fork

```bash
# Note: make sure main is up to date
git pull origin main

git checkout <your-feature-branch>
git rebase main

# IMPORTANT: trick to avoid issues when pushing
git push --force-with-lease origin your-feature-branch
```

from Claude.AI
```
Using `--force` is necessary because rebasing rewrites history. If you're working with others on the same branch, use `--force-with-lease` instead for safety.

I recommend using `--force-with-lease` instead of just `--force` as it's safer - it will fail if someone else has pushed new changes to the branch while you were rebasing.
```


Usually VsCode complains with:
- N pull commit = the same number of commits as originally in your branch
- N push commit = `your rebased commits`

Still the PR will only have the commits that were originally in your branch.

If you 