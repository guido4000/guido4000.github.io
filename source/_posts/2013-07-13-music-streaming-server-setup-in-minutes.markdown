---
layout: post
title: "Music Streaming Server Setup in Minutes"
date: 2013-07-13 15:34
comments: true
categories: 
---

{% img http://placekitten.com/890/190 %}

The Fast Track Setup Guideline
==============================

for setting up CherryMusic on Arch Linux

## 1. Create Arch Linux System on DigitalOcean

Create account on [DigitalOcean](http://www.digitalocean.com/)

Upload your public key (just for convenience)

<!-- more -->

Create an Arch Linux 64bit Droplet

Connect: 

	$ ssh root@[yourdropletip] 


## 2. Configure user

Create user: 

	$ useradd serv
	$ passwd serv

Prevent SSH login for root

	$ nano /etc/ssh/sshd_config  # uncomment PermitRootLogin no


## 3. Install dependencies
Ensure base-devel is installed: 

	$ pacman -S base-revel

Install packages

	$ pacman -Scc
	$ pacman -Syy
	$ pacman -S imagemagick
	$ pacman -S python
	$ pacman -S python-cherrypy
	$ pacman -S ffmpeg
	$ pacman -S lame
	$ pacman -S vorbis-tools
	$ pacman -S sqlite3

## 4. Install app

Install package: 
https://aur.archlinux.org/packages/cherrymusic/

	$ mkdir builds
	$ cd builds
	$ curl -O https://aur.archlinux.org/packages/ch/cherrymusic/cherrymusic.tar.gz
	$ tar -xzf cherrymusic.tar.gz
	$ makepkg -s
	$ pacman -U cherrymusic-0.25.2-1-any.pkg.tar.xz

## 5. Configure app

Edit the conf file manually

	/user/.config/cherrymusic/cherrymusic.conf

or run autoconfigure

	$ cherrymusic --setup --port 8080

## 6. Autorun daemon
Setup the autorun daemon for your user 
	
	$ sudo systemctl start cherrymusic@USER.service
	$ sudo systemctl enable cherrymusic@USER.service

