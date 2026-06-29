# GitHub Pages Deployment Guide

## Overview

**GitHub Pages** is a static site hosting service provided by GitHub. It allows you to publish websites directly from a repository without any server configuration.

It is commonly used for:

* Documentation
* Portfolios
* Landing pages
* Static web projects

The site automatically updates when changes are pushed to the repository.

---

## Table of Contents

- [Quick Start](#quick-start)
- [Requirements](#requirements)
- [Create a Repository](#create-a-repository)
- [Initialize Project](#initialize-project)
- [Connect to GitHub](#connect-to-github)
- [Enable GitHub Pages](#enable-github-pages)
- [Project Structure](#project-structure)
- [Common Issues](#common-issues)

---

## Quick Start

### Minimal deployment workflow

```bash id="gh-en-1"
git init
git add .
git commit -m "initial commit"
git branch -M main
git remote add origin https://github.com/USERNAME/REPOSITORY.git
git push -u origin main
```

---

### Enable GitHub Pages

1. Open your repository on GitHub
2. Go to **Settings**
3. Navigate to **Pages**
4. Under "Build and deployment":

   * Source: `Deploy from branch`
   * Branch: `main`
   * Folder: `/ (root)`
5. Click **Save**

---

## Requirements

Before deploying, make sure you have:

* A GitHub account
* Git installed locally
* A project with an `index.html` file

> ⚠️ GitHub Pages only supports static websites (HTML, CSS, JavaScript)

---

## Create a Repository

1. Go to GitHub
2. Click **New repository**
3. Set:

   * Repository name
   * Visibility (Public or Private)

Optional:

* README file
* .gitignore
* License

---

## Initialize Project

Inside your project folder:

```bash id="gh-en-2"
git init
```

Add files:

```bash id="gh-en-3"
git add .
git commit -m "initial commit"
```

---

## Connect to GitHub

Link your local repository to GitHub:

```bash id="gh-en-4"
git remote add origin https://github.com/USERNAME/REPOSITORY.git
```

Push changes:

```bash id="gh-en-5"
git push -u origin main
```

---

## Enable GitHub Pages

After pushing your code:

1. Open repository settings
2. Navigate to **Pages**
3. Select branch `main`
4. Click **Save**

Your site will be available within 1–5 minutes.

---

## Project Structure

Recommended structure:

```text id="gh-en-6"
project/
│
├── index.html
├── styles.css
├── script.js
└── README.md
```

> ⚠️ The `index.html` file must be placed in the root directory

---

## Common Issues

### Site not accessible

Check:

* GitHub Pages is enabled
* Correct branch is selected (`main`)
* `index.html` exists in root

---

### “fatal: not a git repository”

```text id="gh-en-7"
fatal: not a git repository
```

Fix:

```bash id="gh-en-8"
git init
```

---

### Changes not appearing

Possible solutions:

* Wait 1–5 minutes
* Refresh browser
* Ensure `git push` was successful

---

### Incorrect URL

Verify:

* GitHub username is correct
* Repository name matches URL

---

## Best Practices

### Use meaningful commit messages

```bash id="gh-en-9"
git commit -m "add landing page layout"
```

---

### Keep a clean structure

* Ensure `index.html` is in root
* Avoid unnecessary nested folders

---

### Optional: use branches for development

```bash id="gh-en-10"
git checkout -b dev
```

---

## Conclusion

GitHub Pages provides a simple and reliable way to deploy static websites directly from GitHub repositories.

It is ideal for:

* Portfolios
* Documentation
* Static web applications
