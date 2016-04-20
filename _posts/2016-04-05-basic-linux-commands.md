---
layout: post
title: Linux Common Commands
---

# Ubuntu Linux basics

Hey, want to learn some Linux commands? Me neither.

***
<hr class="rule">

## Looking around

List all with attributes and permissions

    ls -la

List files with size

    ls -h

***

## Moving around

Remove folder and all files with no prompt

    rm -rf folder-name

Rename folder or files

    mv old-name new-name

Move file somewhere else

    mv file-name /somewhere-else

Move folder somewhere else

    mv -R folder-name /somewhere-else

***

## Add a new user with root privileges

Login as root and type:

    adduser newuser

Follow the prompt and create a strong password. Now add the new user to the sudo group.

    gpasswd -a newuser sudo

***

## Configure SSH Daemon

Modify the SSH daemon configuration (the program that allows remote login) to disallow remote SSH access to the root account. Based on a typical [digital ocean](https://www.digitalocean.com/help/getting-started/setting-up-your-server/) setup.

Open the configuration file:

    nano /etc/ssh/sshd_config

Locate line:

    PermitRootLogin yes

Modify this line to:

    PermitRootLogin no

**Reload SSH**

    service ssh restart
