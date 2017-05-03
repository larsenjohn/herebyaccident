---
layout: post
title: Vagrant Scotchbox LAMP stack
---

# Vagrant &amp; Scotchbox LAMP stack

Scotchbox 2.5 Open LAMP stack, by the generous folks at [scotch.io](https://scotch.io/).

***
<hr class="rule">

## Vagrant

Download the [latest and greatest](https://www.vagrantup.com/downloads.html).

<hr class="rule">

## Scotchbox

Get the lastest [Scotchbox](https://box.scotch.io/). Since version 2.5 there is a connection bork, so drop this in the `.vagrant`file.

```
config.ssh.username = "vagrant"
config.ssh.password = "vagrant"
```

Then set up the port forwarding in the `.vagrant` file to whatever works. For example host: 9999, if 8080 is occupied.

```
config.vm.network :forwarded_port, guest: 80, host: 8080
```

Start it up.

```
vagrant up
```

Reload it if it doesn't fire the first time.

```
vagrant reload
```

***
***
