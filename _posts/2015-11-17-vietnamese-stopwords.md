---
layout: post
title: "Vietnamse stopwords dictionary"
date: 2015-11-17 12:58:00 + 0700
category: ml
tags: nodejs, machine learning
---

# Vietnamse stopwords dictionary

> Project site: [https://vietnamese-stopwords.jslab.xyz](https://vietnamese-stopwords.jslab.xyz)

# Using 

### Method 1
Copy `vietname-stopwords.txt` data file to your project.

### Method 2
Using in Nodejs project

1. Install by `npm`
{% highlight sh %}
npm install vietnamese-stopwords
{% endhighlight %}

2. Require in Nodejs code
{% highlight js %}
var stopwords = require('vietnamese-stopwords');

console.log(stopwords);
// [ 'bị', 'bởi', 'cả', 'các', 'cái', ...]
{% endhighlight %}

# How to contribute
1. Fork the project on Github
2. Create a topic branch for your changes
3. Ensure that you provide documentation and test coverage for your changes (patches won’t be accepted without)
4. Create a pull request on Github (these are also a great place to start a conversation around a patch as early as possible)

# Source

* {% include icon-github.html username="duyetdev" %} / [vietnamese-stopwords](http://github.com/duyetdev/vietnamese-stopwords)
* [LICENSE](https://github.com/duyetdev/vietnamese-stopwords#license)
