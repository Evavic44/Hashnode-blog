---
title: "How to Create a GitHub Repository from your Terminal"
seoDescription: "Learn how to create and manage GitHub repositories directly from your terminal using GitHub CLI."
datePublished: Sun Jun 30 2024 14:24:56 GMT+0000 (Coordinated Universal Time)
cuid: cly1n7kyy00060al0feswfx1r
slug: create-github-repository-from-your-terminal
canonical: https://victoreke.com/blog/create-github-repository-from-your-terminal
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1719757480066/5298e48f-269b-4c6c-a5fb-b177b3256567.jpeg
tags: github, terminal, git, cli

---

Managing GitHub repositories from your terminal can significantly enhance your development workflow. By using the command line, you can quickly create and initialize repositories, manage commits, and push changes without relying on a graphical interface. This guide will take you step-by-step through the process, making it easy to harness the power of Git and GitHub directly from your terminal.

## Install GitHub CLI

[GitHub CLI](https://cli.github.com/), or `gh`, is an open-source command-line interface to GitHub for use in your terminal or your scripts. You need to install it into your PC to start using it. Visit the link above to download and install it into your machine.

## Create a New Repository

Open up a terminal and run the below command to create a new repository:

```bash
gh repo create
```

This will prompt an interactive window you can use to configure your repository details.

```bash
What would you like to do? Create a new repository on GitHub from scratch
? Repository name test

? Repository name test
? Repository owner Evavic44
? Description Testing GitHub CLI

? Description Testing GitHub CLI
? Visibility Public
? Would you like to add a README file? Yes
? Would you like to add a .gitignore? Yes
? Would you like to add a license? Yes
? This will create "test" as a public repository on GitHub. Continue? Yes
✓ Created repository Evavic44/test on GitHub
  https://github.com/Evavic44/test-cli
? Clone the new repository locally? No
```

Once completed, you should have your repository successfully created on GitHub. Now you can point your local project to the remote branch and push it to GitHub.

```bash
git remote add origin https://github.com/Evavic44/test.git
git add .
git commit -m 'Initial commit'
git push origin main
```

If you choose to create a `README` or `License` file during the `gh repo create` set-up, trying to pull it into a local project will obviously throw an error due to unrelated histories between the remote and local branch.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1719756207187/db6888bc-225e-405e-842e-493e1dc4e485.png align="left")

To resolve this, you can force the merging using the below command:

```bash
git pull origin main --allow-unrelated-histories
```

If you get any conflicts, simply fix it, commit and then push to GitHub.

Aside form creating a new repository, you can perform other operations using the GitHub CLI tool. Visit [GitHub CLI Commands](https://cli.github.com/manual/gh) to see an exhaustive list.