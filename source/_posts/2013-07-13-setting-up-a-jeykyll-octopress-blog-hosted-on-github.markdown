---
layout: post
title: "Setting up a Jeykyll Octopress Blog hosted on github"
date: 2013-07-13 09:34
comments: true
categories: [Static, HTML5]
---

The 5 Minute Setup Guideline
============================

### 1. Get and install Octopress

	$ git clone git://github.com/imathis/octopress.git octopress
	$ ruby --version # should report Ruby 1.9.3
	$ gem install bundler
	$ rbenv hash
	$ bundle install
	$ rake install

<!-- more -->

Link: [Octopress setup](http://octopress.org/docs/setup/) 

### 2. Setup your github page

Create a new repository [Github](https://github.com/repositories/new)

Autoconfigure:
	$ rake setup_github_pages
Link: [Octopress github setup](http://octopress.org/docs/deploying/github/) 

### 3. Deploy

	$ rake setup_github_pages

	$ rake generate
	$ rake deploy

### 4. Commit your code

	$ git add .
	$ git commit -m "initial deploy"
	$ git push origin source

### 5. Configure your blog

The main config files
	_config.yml # Main config (Jekyll's settings)
	Rakefile # Configs for deployment
	config.rb # Compass config
	config.ru # Rack config

[Octopress configure](http://octopress.org/docs/configuring/) 

### 6. Create a blog post

	$ rake new_post["title"]

[Octopress blogging](http://octopress.org/docs/blogging/) 

### 7. Create a page

	$ rake new_page[super-awesome]

### 8. Check it out

	$ rake generate

	Local: $ rake preview
	Github: $ rake deploy

