# csr-root

---

This repository contains all necessary modules to start csr locally.

Before working download necessary tools:
- [git-bash](https://git-scm.com/downloads) (for windows)
- [docker](https://docs.docker.com/desktop/)
- [create ssh key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) (you can not add a password for key) and ad it to [github](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)

Clone repository:

``git clone git@github.com:CSR-LC/csr-root.git``

Initialise and update submodules:

``git submodule update --init``

Now you have all repository updated and ready to work.

After you need to select branch to work and checkout. There are two-way to do it:  

## First

Select branch in each repo:

``git submodule set-branch --branch <your branch> <repo path>``

In the end checkout and update all submodules to selected branch:

`` git submodule update --remote``

Now you have repository with selected updated branch. You can use previous command to get updates from remote.

## Second 

Enter to each directory add checkout to  branch: 

```
cd <repo_path>
git checkout <branch>
git pull
cd ..
```

In the future, you can use next command to update all repositories:

``git submodule foreach git pull``

---
# Start application

Check files . It should contain:

csr-be/config.json
```json
  "db": {
    "host": "csr-db",
    "port": "5432",
    "user": "csr",
    "database": "csr",
    "showSql": false
  },

```
csr-fe/src/environments/environment.ts
```json
export const environment = {
  production: false,
  apiUrl: 'http://localhost:8080/api/',
};
```
csr-fe/src/proxy.conf.json
```json
"/api/*": {
      "target": "http://localhost:8080/api/",
      "secure": true,
      "changeOrigin": true,
      "logLevel": "debug"
```

Build images:

``docker compose build --no-cache``

if you want to rebuild one service add it name in the end of previous command.

Start application:

``docker compoce up``

add -d after **up** if to start app in detached mode.

Stop application:

``docker compose stop``

Delete containers:

``docker compoose down``
