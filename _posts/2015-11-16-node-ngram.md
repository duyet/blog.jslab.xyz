---
layout: post
title:  "Nodejs - Ngram for Nodejs."
date:   2015-11-16 01:38:00 +0700
category: nodejs
tags: nodejs
---

Ngram for Nodejs.

[![NPM](https://nodei.co/npm/node-ngram.png?downloads=true&downloadRank=true&stars=true)](https://nodei.co/npm/node-ngram/)

# Instalation 

{% highlight js %}
npm install node-ngram
{% endhighlight %}

# Example

{% highlight js %}
var Ngram = require('node-ngram');

var ngram = new Ngram({
	n: 2
});

console.log(ngram.ngram("Le Van Duyet"));
// => [["Le", "Van"], ["Van", "Duyet"]]

console.log(ngram.ngram("Le Van Duyet", 3));
// => [ [ 'le', 'van', 'duyet' ], [ 'van', 'duyet' ], [ 'duyet' ] ]

console.log(ngram.trigram("Van-Duyet Le Developer from Vietnam"));
// => [ [ 'van-duyet', 'le' ],
//  [ 'le', 'developer' ],
//  [ 'developer', 'from' ],
//  [ 'from', 'vietnam' ],
//  [ 'vietnam' ] ]

console.log(ngram.ngram("Neque porro quisquam est quitur, adipisci velit."));
// => [ [ 'neque', 'porro' ],
//  [ 'porro', 'quisquam' ],
//  [ 'quisquam', 'est' ],
//  [ 'est', 'quitur' ],
//  [ 'quitur', 'adipisci' ],
//  [ 'adipisci', 'velit' ],
//  [ 'velit' ] ]
{% endhighlight %}

# Test
{% highlight sh %}
npm test
{% endhighlight %}

# How to contribute
1. Fork the project on Github
2. Create a topic branch for your changes
3. Ensure that you provide documentation and test coverage for your changes (patches won’t be accepted without)
4. Create a pull request on Github (these are also a great place to start a conversation around a patch as early as possible)

# Source

* {% include icon-github.html username="duyetdev" %} / [node-ngram](http://github.com/duyetdev/node-ngram)
* [LICENSE](https://github.com/duyetdev/node-ngram/blob/master/LICENSE)