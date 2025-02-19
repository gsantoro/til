# Git - checkout symlinks
MacOS doesn't checkout out symlinks by default. You can enable this feature with

```bash
git config core.symlinks true
```

If you have already some symlinks that are pointing nowhere, you might get a `typechange: <filename>` message when doing `git status`.

you will need to `git checkout` any of those typechanges to fix it.