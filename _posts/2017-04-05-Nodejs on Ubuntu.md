---
title: Deploy Node.js on Ubuntu
layout: post
description: Start to creat your own site.

---

> Start to creat your own site.



## Install Node.js

```bash
$ sudo apt-get install nodejs
```

the `nodejs` package contains the `nodejs` binary as well as `npm`. You can run `node -v` and `npm -v` to see the version.



## Install [PM2](http://pm2.keymetrics.io)

PM2 is a production process manager for Node.js applications with a built-in load balancer. It allows you to keep applications alive forever, to reload them without downtime and to facilitate common system admin tasks.

Run this command to install PM2:

```bash
$ sudo npm install -g pm2
```

PM2 usage:

```bash
$ pm2 start app.js
$ pm2 monit
$ pm2 list
$ pm2 stop    
$ pm2 restart 
$ pm2 delete  
```

 

## Install Nginx

Install Nginx using apt-get:

```bash
$ sudo apt-get install nginx
```

Modify nginx config:

```bash
$ sudo vim /etc/nginx/nginx.conf
```

Add:

```bash
upstream riki {
	server 127.0.0.1:[YOUR PORT];
}

server {
	listen 80;
	server_name localhost;
	
	location / {
		proxy_pass http://riki;
	}
}
```

save and exit.

Next, restart Nginx:

```bash
$ sudo systemctl restart nginx
```



Enjoy your website~