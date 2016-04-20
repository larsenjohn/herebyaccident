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

<hr class="rule">

***

# Server settings

Based on a typical [digitalocean](https://www.digitalocean.com/help/getting-started/setting-up-your-server/) Ubuntu droplet. There are also some good resources to look into at [Linode](https://www.linode.com/docs/security/securing-your-server), depending on how each is deployed.

***

## Add a new user with root privileges

Login as root and type:

    adduser newuser

Follow the prompt and create a strong password. Now add the new user to the sudo group.

    gpasswd -a newuser sudo

***

## Configure SSH Daemon

Modify the SSH daemon configuration (the program that allows remote login) to disallow remote SSH access to the root account.

Open the configuration file:

    nano /etc/ssh/sshd_config

Locate line:

    PermitRootLogin yes

Modify this line to:

    PermitRootLogin no

**Reload SSH**

    service ssh restart

***

## Configure Uncomplicated Firewall (ufw)

This sets up the bare minimum without SSL/TLS or SMTP opened. Full config docs from digitalocean is over [here](https://www.digitalocean.com/community/tutorials/how-to-setup-a-firewall-with-ufw-on-an-ubuntu-and-debian-cloud-server).

Create an exception for SSH connections so that we can maintain access for remote administration.

The SSH daemon runs on port 22 by default and `ufw` can implement a rule by name if the default has not been changed. So if you have not modified SSH port, you can enable the exception by typing:

    sudo ufw allow ssh

Allow only specific IP addresses if you want:

    sudo ufw allow from 192.168.255.255

Allow access to port 80 for a HTTP web server:

    sudo ufw allow 80/tcp

Review selections:

    sudo ufw show added

Enable firewall:

    sudo ufw enable

Check status:

    sudo ufw status verbose
