---
title: "Using multiple github accounts with ssh keys"
description: "Using multiple github accounts with ssh keys"
date: 2026-01-20
tags: [git,ssh,howto]
categories: [howto]
---

Using multiple github accounts with ssh keys.

1.  [Generate ssh key pairs for accounts](https://help.github.com/articles/generating-a-new-ssh-key/) and [add them to GitHub accounts](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/).
    
2.  Edit/Create ssh config file (`~/.ssh/config`):
    
    ```
    # Default github account: oanhnn
    Host github.com
       HostName github.com
       IdentityFile ~/.ssh/oanhnn_private_key
       IdentitiesOnly yes
       
    # Other github account: superman
    Host github-superman
       HostName github.com
       IdentityFile ~/.ssh/superman_private_key
       IdentitiesOnly yes
    ```
    
    > NOTE: If you use any account frequently, you should use the default hostname (`github.com`).
    
3.  [Add ssh private keys to your agent](https://help.github.com/articles/adding-a-new-ssh-key-to-the-ssh-agent/):
    
    ```shell
    $ ssh-add ~/.ssh/oanhnn_private_key
    $ ssh-add ~/.ssh/superman_private_key
    ```
    
4.  Test your connection
    
    ```shell
    $ ssh-keyscan github.com >> ~/.ssh/known_hosts
    $ ssh -T git@github.com
    $ ssh -T git@github-superman
    ```
    
    If everything is OK, you will see these messages:
    
    ```shell
    Hi oanhnn! You've successfully authenticated, but GitHub does not provide shell access.
    ```
    
    ```shell
    Hi superman! You've successfully authenticated, but GitHub does not provide shell access.
    ```
    
1.  Now all are set, you need remember
    
    ```
    git@github-superman:org/project.git => user is superman
    git@github.com:org/project.git.     => user is oanhnn
    ```
    

-   If you need clone a repository, just do:

```shell
$ git clone git@github-superman:org1/project1.git /path/to/project1
$ cd /path/to/project1
$ git config user.email "superman@example.com"
$ git config user.name  "Super Man"
```

-   If you already have the repo set up, after the ssh config instructions, you need change the URL of `origin`, just do:

```
$ cd /path/to/project2
$ git remote set-url origin git@github-superman:org2/project2.git
$ git config user.email "superman@example.com"
$ git config user.name  "Super Man"
```

-   If you are creating a new repository on local:

```
$ cd /path/to/project3
$ git init
$ git remote add origin git@github-superman:org3/project3.git
$ git config user.email "superman@example.com"
$ git config user.name  "Super Man"
$ git add .
$ git commit -m "Initial commit"
$ git push -u origin master
```

There's also [Git Identity Switcher](https://github.com/csawai/git-identity-switcher) but I've not really tried that yet.