---
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.svg')
marp: true
---

![bg left:40% 60%](./images/rawlabs-academy-logo.png)

# **Git**

Versioning Control and Branch Management

---
<!-- _class: lead -->
# What is Versioning?


Control the source code version

---
<!-- _class: lead -->
# The Problem
</br>

![w:1000 center](./images/git/versioning-problem.png)

*Revision is a **must**, don't expect every code is **perfect***

---
# What is Git?
<!-- _class: lead -->
![center](./images/git/git-logo.png)

One of the popular **version control system** used by **developers** to develop software **together**.

---
<!-- _class: lead -->
# Everyone **Should Sync to The Remote Server**
![center](./images/git/git-simulation.png)

---
# Git **Track** Every File Change
<!-- _class: lead -->
![w:200 center](./images/git/files.png)

Your changes, John's changes and everyone changes can be tracked by git

---
# Install Git **On Mac**

1. Download latest [Git for Mac Installer](https://sourceforge.net/projects/git-osx-installer/files/)
2. Follow the prompts to install git
3. Open a terminal and verify the installation was successful by typing `git --version`

```bash
$ git --version
git version 2.35.1
```
---
# Install Git **On Windows**
1. Download latest [Git for Mac Installer](https://git-for-windows.github.io/)
2. When you've successfully started the installer, you should see the Git Setup wizard screen. Follow the Next and Finish prompts to complete the installation. The default options are pretty sensible for most users
3. Open a Command Prompt (or Git Bash if during installation you elected not to use Git from the Windows Command Prompt)

---
# Install Git **On Linux**
1. From your shell, install git using `apt-get`
    ```bash
    $ sudo apt-get update
    $ sudo apt-get install git
    ```
2. Verify the installation was successful by typing `git --version`
    ```bash
    $ git --version
    git version 2.35.1
    ```

---
# Git Configuration
### GIT **INIT, CLONE, CONFIG**

```bash
## Git Global Configuration
$ git config --global user.name "John Doe"
$ git config --global user.email "johndoe@example.com"

## Git Initialization
$ git init
$ git remote add <REMOTE_NAME> <REMOTE_REPOSITORY_URL>
$ git push -u <REMOTE_NAME> <LOCAL_BRANCH_NAME>

## Start with existing project, start working on the project
$ git clone <REMOTE_REPOSITORY_URL> myproject
$ cd myproject
```

---
# **Staging** Area
<!-- _class: lead -->
![w:1000 center](./images/git/staging-area.png)

---
# Commit **Message**

If applied, this commit will be **your subject line here**
Better writing commit message with writing convention based on this [reference](https://medium.com/swlh/writing-better-commit-messages-9b0b6ff60c67).

Type of commit :
```bash
feat:       The new feature being added to a particular application
fix:        A bug fix (this correlates with PATCH in SemVer)
style:      Feature and updates related to styling
refactor:   Refactoring a specific section of the codebase
test:       Everything related to testing
docs:       Everything related to documentation
chore:      Regular code maintenance
```

---
# Synchronizing Git **Push, Fetch, & Pull**

```bash
## Git remote
$ git remote -v
$ git remote add origin https://github.com/example.git

## Fetch and pull
$ git fetch --all
$ git pull origin master

## Push
$ git push origin master
$ git push origin feature/login-user
```

---
# Git **Branching**

```bash
## Show all branch list
$ git branch

## Create new branch
$ git branch feature/registration
$ git checkout feature/registration

## Force delete specified branch
$ git branch -D <BRANCH_NAME>

## List remote branch
$ git branch -a
```

---
# Pull **Request**
![w:1150 center](./images/git/pull-request.png)

---
# **Workflow** Collaboration
<!-- _class: lead -->
![w:400 center](./images/git/workflow.svg)

---
# Do you work like this?
<!-- _class: lead -->
![w:1100 center](./images/git/single-branch.png)

---
# Or like this?
<!-- _class: lead -->
![w:1100 center](./images/git/feature-branch.png)

---
# The **best way** like this
<!-- _class: lead -->
![w:1100 center](./images/git/git-flow-branch.png)

---
# Let the **Master Branch** Undisturbed
![w:600 center](./images/git/keep-master-undisturbed.png)

```bash
$ (master) git branch development
$ (master) git checkout development
```

---
# Avoid **Direct Edit** on Development
![w:320 center](./images/git/avoid-direct-edit-on-development.png)

```bash
$ (development) git branch feature/new-feature
$ (development) git checkout feature/new-feature
```

---
# Apply **Feature** into Development Only
![w:700 center](./images/git/apply-feature-to-development.png)

```bash
$ (feature/new-feature) git checkout development
$ (development) git merge feature/new-feature
```

---
# Apply **Development** into Master
**When it's already done**

![w:900 center](./images/git/apply-development-to-master.png)

```bash
$ (master) git merge development
```

---
# Any **Question**
<!-- _class: lead -->
![w:400 center](./images/question-mark.png)