---
layout: post
title:  "Static HTML Server"
date:   2015-11-16 01:22:00 +0700
category: post
tags: nodejs
---

# Static HTML Server

[![NPM](https://nodei.co/npm/static-html-server.png?downloads=true&downloadRank=true&stars=true)](https://nodei.co/npm/static-html-server/)

Simple static web server.

### Install

{% highlight sh %}
npm install static-html-server -g
{% endhighlight %}

### Usage


{% highlight sh %}
static-html-server -p [port] -r [root folder] -f [fallback path if not found]
{% endhighlight %}

Arguments (all are optional):

* `p`: [`Number`] port number, default to 8000
* `r`: [`String`] root folder, default to working directory
* `f`: [`String`] fallback path when page not found, default to not falling back and send 404

For example
{% highlight sh %}
static-html-server -p 8899 -r ./ -f index.html
Server running at http://localhost:8899/ [root: ./, fallback: index.html]
{% endhighlight %}

# Source

{% include icon-github.html username="duyetdev" %} / [static-html-server](static-html-server)
