---
layout: post
title: AWS EC2 LEMP stack
---

# AWS EC2 LEMP stack with easyengine.io

The [easyengine](https://easyengine.io/) setup is so simple it's kind of scary. I really have no idea what to do if I got into trouble with it, but for now it's a magical little rainbow.

***
<hr class="rule">

## Spin up an EC2 instance

Launch an Ubuntu Server 14.04 LTS instance. Use all of the default settings. When you get to the **security groups** add these custom rules after the auto populated ssh.

1. SSH, TCP, 22, anywhere
2. HTTP, TCP, 80, anywhere
3. HTTPS, TCP, 443, anywhere
4. Custom TCP rule, TCP, 2222, anywhere
5. Custom ICMP rule, Echo Reply, N/A, anywhere

Change the permissions on the `.pem` file

```
chmod 600 key.pem
```

<hr class="rule">

## Install easyengine

Connect to the instance and run

```
wget -qO ee rt.cx/ee && sudo bash ee
```

<hr class="rule">

## Create a site

This will roll a site and configure the virtual host in one swoop.

Static

```
ee site create example.com --html
```

PHP+MySQL.

MySQL database details will be in the `ee-config.php` file.

```
ee site create example.com --mysql
```

Standard Wordpress

```
ee site create example.com --wp # install wordpress without any page caching
ee site create example.com --w3tc # install wordpress with w3-total-cache plugin
ee site create example.com --wpsc # install wordpress with whisp-super-cache plugin
ee site create example.com --wpfc # install wordpress + nginx fastcgi_cache
ee site create example.com --wpredis # install wordpress + nginx redis_cache
```

***

## Delete a site

```
ee site delete example.com
```

Delete webroot only

```
ee site delete example.com --files
```

Delete db only

```
ee site delete example.com --db
```

***

## Restart

```
ee stack restart
```

and reload

```
ee stack reload
```

***

## Update

```
ee update
```
