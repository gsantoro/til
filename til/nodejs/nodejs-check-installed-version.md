---
title: nodejs-install-version
draft: false
tags:
---
# nodejs-check-installed-version
How to check which version is installed of a package. you have a few options:

1. Use `npm list`:text
    `npm list <library>`
    This will show the installed version of the specified library in your project.
2. Check `package.json`: Open your project's `package.json` file and look for the library in the `dependencies` or `devDependencies` section.
3. Use `npm ls <library>`. This is similar to `npm list` but can provide more detailed information.
4. Check directly in `node_modules`,You can look at the `package.json` file of the library in the `cat node_modules/<library>/package.json | grep version`
5. Use `npm outdated <library>`. This will show the current version, wanted version, and latest version.
6. For global packages, if you're looking for a globally installed package, use: `npm list -g <library>`
