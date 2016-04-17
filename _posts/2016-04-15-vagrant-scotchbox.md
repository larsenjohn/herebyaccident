---
layout: post
title: Vagrant Scotchbox LAMP stack
---

# Vagrant &amp; Scotchbox LAMP stack

I'm pretty lazy as lazy people go. The nice folks over at [scotch](https://scotch.io/) have done a lot of work for me. Maybe someday I'll buy them something nice.

***
<hr class="rule">

## Vagrant

Go get it again. [You know the drill](https://www.vagrantup.com/downloads.html).

<hr class="rule">

## Scotchbox

As always, check if it's [still alive](https://box.scotch.io/). Since version 2.5 you should remember the bork, and drop this in the <code>.vagrant</code> file.

<pre>
config.ssh.username = "vagrant"
config.ssh.password = "vagrant"
</pre>

Then set up the port forwarding to whatever works.

<pre>
config.vm.network :forwarded_port, guest: 80, host: 8080
</pre>

<hr class="rule">
