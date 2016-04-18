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

Get the lastest [Scotchbox](https://box.scotch.io/). Since version 2.5 there is a connection bork, so drop this in the <code>.vagrant</code> file.

<pre>
config.ssh.username = "vagrant"
config.ssh.password = "vagrant"
</pre>

Then set up the port forwarding to whatever works.

<pre>
config.vm.network :forwarded_port, guest: 80, host: 8080
</pre>

Reload it if it doesn't fire the first time.

<pre>
vagrant reload
</pre>

<hr class="rule">
