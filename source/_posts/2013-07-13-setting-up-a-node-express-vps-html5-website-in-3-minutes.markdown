---
layout: post
title: "Setting up a Node Express VPS HTML5 Website in 3 Minutes"
date: 2013-07-13 10:16
comments: true
categories: [Node, HTML5, Express]
---

{% img http://placekitten.com/890/280 %}

The 3 Minute Setup Guideline
============================

boot up an EC2 instance with a node webserver and an HTML5 template in minutes


## 1. Get EC2 instance with one click

Free 30 minute one click server <http://www.instantserver.io>

<!-- more -->
                        
For a more permanent solution check out <https://www.digitalocean.com>

## 2. Install node for ubuntu
Reference <https://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager#ubuntu-mint>

	$ sudo apt-get update
	$ sudo apt-get install python-software-properties python g++ make
	optional $ sudo apt-get install software-properties-common
	$ sudo add-apt-repository ppa:chris-lea/node.js
	$ sudo apt-get update
	$ sudo apt-get install nodejs

## 3. Install connect
<http://stackoverflow.com/questions/6084360/node-js-as-a-simple-web-server>

a) Install connect with NPM
	
	$ npm install connect

b) Create server.js file with this content:

	var connect = require('connect');
	connect.createServer(
    	connect.static(__dirname)
	).listen(8080);


c) Run with NodeJS
	
	$ node server.js

## 4. Copy HTML5 Boilerplate
<http://html5boilerplate.com/>

Download boilerplate and copy to server

## 5. Open Website
Open up the server IP in the browser on port 8080

Done!

## 6. Run the server forever
	$ npm install forever -g
	$ forever start -l forever.log -o out.log -e err.log server.js 

Make forever start script on reboot
	$ crontab -u root -e 
		@reboot /usr/lib/node_modules/forever/bin/forever start /root/server.js 
	