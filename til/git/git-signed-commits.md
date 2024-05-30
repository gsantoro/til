---
title: Git signed commits
draft: true
tags: 

---
# Git signed commits
To sign a Git commit, you can use the following command

```shell
git commit -S -m "YOUR_COMMIT_MESSAGE"
```
But before running that command, you need to tell Git which type of key to use.

You have two main alternatives.
- an SSH key, an easier solution since you can reuse an existing SSH key, and there is no need for a passphrase
- a GPG key, it requires generating a GPG key and a passphrase

More info at [signing commits](https://docs.github.com/en/authentication/managing-commit-signature-verification/signing-commits).

## Sign Git commits with SSH key
You can run the following commands:

```bash
git config --global commit.gpgsign true
git config --global gpg.format ssh
git config --global user.signingkey ~/.ssh/id_ed25519.pub
```

You might need to adapt the previous command to point to a different SSH public key.

More info at [telling git about your ssh key](https://docs.github.com/en/authentication/managing-commit-signature-verification/telling-git-about-your-signing-key#telling-git-about-your-ssh-key).

IMPORTANT:
What GitHub fails to say in the documentation is that even if you have already added the SSH key to your GitHub account (probably as an "Authentication key" since that is the default option), you need that same key as a "Signing key" as well; otherwise, your signed commit will be "unverified."

## Sign Git commits with a GPG key
### Add a GPG key to your GitHub account
First, you need to create a new GPG key

```bash
gpg --full-generate-key
```
You can use the default encryption algorithms. You must also provide your full name, a valid email, and a passphrase. For more information on the topic, see [generating a new GPG key](https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key).

Once your GPG key has been created, You can list it with the following command:

```bash
gpg --list-secret-keys --keyid-format=long
```

To export your GPG key to GitHub, you can use the following commands:

```bash
KEY_ID=$(gpg --list-secret-keys --keyid-format LONG | awk '/^sec/ {split($2, a, "/"); print a[2]}')
gpg --armor --export ${KEY_ID}
```

You need to copy the previous command's output to your GitHub account. More info at [adding a GPG key to your GitHub account](https://docs.github.com/en/authentication/managing-commit-signature-verification/adding-a-gpg-key-to-your-github-account)

### Sign all your commits with a GPG key
You can configure Git to sign all your commits with the following commands:

```shell
git config --global commit.gpgsign true
KEY_ID=$(gpg --list-secret-keys --keyid-format LONG | awk '/^sec/ {split($2, a, "/"); print a[2]}')
git config --global user.signingkey ${KEY_ID}
```

If later on, you want to disable signing all your commits you can run;

```shell
git config --global commit.gpgsign false
```

If you need more help, go to [telling Git about your signing key](https://docs.github.com/en/authentication/managing-commit-signature-verification/telling-git-about-your-signing-key).

If you're using GPG, after you create your commit, you need to provide the passphrase you used to create the GPG key.

To store your GPG key passphrase so you don't have to enter it every time you sign a commit, we recommend using the following tools:

- For Mac users, the [GPG Suite](https://gpgtools.org/) allows you to store your GPG key passphrase in the macOS Keychain.
- For Windows users, the [Gpg4win](https://www.gpg4win.org/) integrates with other Windows tools.
