# csr-root

---

This repository contains all necessary modules to start csr locally.

Before working dowload necccery tools:
- [git-bash](https://git-scm.com/downloads) (for windows)
- [docker](https://docs.docker.com/desktop/)
- [create ssh key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) (you can not add a password for key) and ad it to [github](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)

Clone repository

``git clone git@github.com:CSR-LC/csr-root.git``

Initialisate and update submodules

``git submodules update --init``

Now you have all repository updated and ready to work

After you need to select branch to work and checkout. There are two way to do it  

## First

Select branch in each repo:

``git submodule set-branch --branch <your branch> <repo path>``

In the end checkout and update all submodules to selected branch

`` git submodule update --remote``

Now you have reposetory with selected updated branch. You can use previous command to get updates from remote.

## Second 

Enter to eatch directory add checkout to neccery branch 

```
cd <repo_path>
git checkout <branch>
git pull
cd ..
```

In future you can use next command to update all repositories

``git submodule foreach git pull``

---
# Start application

Build images

``docker compose build --no-cache``

if you want to rebuilt one service add it name in the end of previous command

Start application

``docker compoce up``

add -d after **up** if to start app in datached mode

Stop application

``docker compose stop``

Delete containers

``docker compoose down``
