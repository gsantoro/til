---
title: Git signed commits
draft: true
tags: 

---
# Git signed commits
Create a GPG key

```bash
gpg --full-generate-key
```
You can use the default encryption algorithms. You must also provide your Full name, a valid email and a passphrase—more info at [Generating a new GPG key](https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key).

You can list your GPG keys with the following command:

```bash
gpg --list-secret-keys --keyid-format=long
```

You need to export your GPG key to GitHub

```bash
gpg --armor --export <key_id>
```

For info on how to get the key_id check the documentation at [Generating a new GPG key](https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key).

You need to export your GPG key to GitHub. More info at [Adding a GPG key to your GitHub account](https://docs.github.com/en/authentication/managing-commit-signature-verification/adding-a-gpg-key-to-your-github-account)