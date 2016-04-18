---
layout: post
title: Open VPN El Capitan bug
---

# Open VPN &amp; OSX El Capitan connection bug.

This is always a fun one. Running El Capitan and getting a fucked up error trying to connect to Open VPN? We'll here's a total cludge for your amusement.

***
<hr class="rule">

## csrutil disable

1. Restart to recovery mode: CMD+R.
2. In terminal run:

<pre>
csrutil disable; reboot
</pre>

Do your dirty work, and when it's all clear, you'll need to reboot in recovery once more to zip it back up.

<pre>
csrutil enable
</pre>
