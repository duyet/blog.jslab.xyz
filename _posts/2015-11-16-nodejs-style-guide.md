---
layout: post
title:  "Node.js Style Guide!"
date:   2015-11-16 00:50:49 +0700
category: post
tags: nodejs
---

This is a guide for writing consistent and aesthetically pleasing node.js code. It is inspired by what is popular within the community, and flavored with some personal opinions.
<!--more-->

See the source of this post at {% include icon-github.html username="duyetdev" %} / [node-style-guide](https://github.com/duyetdev/node-style-guide)

# Table of contents

* [1 Tab for indention](#tab-for-indention)
* [Newlines](#newlines)
* [Use Semicolons](#use-semicolons)
* [80 characters per line](#80-characters-per-line)
* [Use single quotes](#use-single-quotes)
* [Opening braces go on the same line](#opening-braces-go-on-the-same-line)
* [Method chaining](#method-chaining)
* [Functions](#functions)
* [Requires](#requires)
* [Always check for errors in callbacks](#always-check-for-errors-in-callbacks)
* [Only throw in synchronous functions](#only-throw-in-synchronous-functions)
* [Catch errors in sync calls](#catch-errors-in-sync-calls)
* [Use FIXME: and TODO: comment to annotate problems](#use-fixme-and-todo-comment-to-annotate-problems)
* [Whitespace rightway](#whitespace-rightway)
* [Declare one variable per var statement](#declare-one-variable-per-var-statement)
* [Use lowerCamelCase for variables, properties and function names](#use-lowercamelcase-for-variables-properties-and-function-names)
* [Use UpperCamelCase for class names](#use-uppercamelcase-for-class-names)
* [Use UPPERCASE for Constants](#use-uppercase-for-constants)
* [Object / Array creation](#object--array-creation)
* [Use the === operator](#use-the--operator)
* [Use multi-line ternary operator](#use-multi-line-ternary-operator)
* [Use slashes for comments](#use-slashes-for-comments)
* [Object.freeze, Object.preventExtensions, Object.seal, with, eval](#objectfreeze-objectpreventextensions-objectseal-with-eval)
* [Getters and setters](#getters-and-setters)

## 1 Tab for indention

Use 1 tab character for indenting your code and swear an oath to never mix tabs and spaces - a special kind of hell is awaiting you otherwise.

## Newlines

Use UNIX-style newlines (`\n`), and a newline character as the last character 
of a file. Windows-style newlines (`\r\n`) are forbidden inside any repository.

## Use Semicolons

According to [scientific research][hnsemicolons], the usage of semicolons is
a core value of our community. Consider the points of [the opposition][], but
be a traditionalist when it comes to abusing error correction mechanisms for
cheap syntactic pleasures.

[the opposition]: http://blog.izs.me/post/2353458699/an-open-letter-to-javascript-leaders-regarding
[hnsemicolons]: http://news.ycombinator.com/item?id=1547647

## 80 characters per line

Limit your lines to 80 characters. Yes, screens have gotten much bigger over the
last few years, but your brain has not. Use the additional room for split screen,
your editor supports that, right?

## Use single quotes

Use single quotes, unless you are writing JSON.

*Right:*

{% highlight js %}
var foo = 'bar';
{% endhighlight %}

*Wrong:*

{% highlight js %}
var foo = "bar";
{% endhighlight %}

## Opening braces go on the same line

Your opening braces go on the same line as the statement.

*Right:*

{% highlight js %}
if (true) {
  console.log('winning');
}
{% endhighlight %}

*Wrong:*

{% highlight js %}
if (true)
{
  console.log('losing');
}
{% endhighlight %}

Also, notice the use of whitespace before and after the condition statement.

## Method chaining

One method per line should be used if you want to chain methods.

You should also indent these methods so it's easier to tell they are part of the same chain.

*Right:*

{% highlight js %}
User
  .findOne({ name: 'foo' })
  .populate('bar')
  .exec(function(err, user) {
    return true;
  });
{% endhighlight %}`

*Wrong:*

{% highlight js %}
User
.findOne({ name: 'foo' })
.populate('bar')
.exec(function(err, user) {
  return true;
});

User.findOne({ name: 'foo' })
  .populate('bar')
  .exec(function(err, user) {
    return true;
  });

User.findOne({ name: 'foo' }).populate('bar')
.exec(function(err, user) {
  return true;
});

User.findOne({ name: 'foo' }).populate('bar')
  .exec(function(err, user) {
    return true;
  });
{% endhighlight %}`

## Functions

* Function expressions:
{% highlight js %}
// anonymous function expression
var anonymous = function() {
  return true;
};

// named function expression
var named = function named() {
  return true;
};

// immediately-invoked function expression (IIFE)
(function() {
  console.log('Welcome to the Internet. Please follow me.');
})();
{% endhighlight %}

* Never declare a function in a non-function block (if, while, etc). Assign the function to a variable instead.
{% highlight js %}
// bad
if (currentUser) {
  function test() {
    console.log('Nope.');
  }
}

// good
var test;
if (currentUser) {
  test = function test() {
    console.log('Yup.');
  };
}
{% endhighlight %}

* Never name a parameter arguments, this will take precedence over the arguments object that is given to every function scope.
{% highlight js %}
// bad
function nope(name, options, arguments) {
  // ...stuff...
}

// good
function yup(name, options, args) {
  // ...stuff...
}
{% endhighlight %}

## Requires
* Organize your node requires in the following order:
  * core modules  
  * npm modules
  * others
  
{% highlight js %}
// good
var http = require('http');
var fs = require('fs');

var async = require('async');
var mongoose = require('mongoose');

var Car = require('./models/Car');


// bad
var Car = require('./models/Car');
var async = require('async');
var http = require('http');
{% endhighlight %}
* Do not use the .js when requiring modules
{% highlight js %}
  // bad
  var Batmobil = require('./models/Car.js');

  // good
  var Batmobil = require('./models/Car');
{% endhighlight %}

## Declare one variable per var statement

Declare one variable per var statement, it makes it easier to re-order the
lines. However, ignore [Crockford][crockfordconvention] when it comes to
declaring variables deeper inside a function, just put the declarations wherever
they make sense.

*Right:*

{% highlight js %}
var keys   = ['foo', 'bar'];
var values = [23, 42];

var object = {};
while (keys.length) {
  var key = keys.pop();
  object[key] = values.pop();
}
{% endhighlight %}

*Wrong:*

{% highlight js %}
var keys = ['foo', 'bar'],
    values = [23, 42],
    object = {},
    key;

while (keys.length) {
  key = keys.pop();
  object[key] = values.pop();
}
{% endhighlight %}

[crockfordconvention]: http://javascript.crockford.com/code.html

## Always check for errors in callbacks

Always check for errors and return if any errors in callbacks

{% highlight js %}
//bad
database.get('pokemons', function(err, pokemons) {
  console.log(pokemons);
});

//good
database.get('drabonballs', function(err, drabonballs) {
  if (err) {
    // handle the error somehow, maybe return with a callback
    return console.log(err);
  }
  console.log(drabonballs);
});
{% endhighlight %}

## Only throw in synchronous functions

Try-catch blocks cannot be used to wrap async code. They will bubble up to to the top, and bring down the entire process.

{% highlight js %}
//bad
function readPackageJson (callback) {
  fs.readFile('package.json', function(err, file) {
    if (err) {
      throw err;
    }
    ...
  });
}

//good
function readPackageJson (callback) {
  fs.readFile('package.json', function(err, file) {
    if (err) {
      // Return the callback error
      return  callback(err);
    }
    ...
  });
}
{% endhighlight %}

## Catch errors in sync calls

{% highlight js %}
//bad
var data = JSON.parse(jsonAsAString);

//good
var data;
try {
  data = JSON.parse(jsonAsAString);
} catch (e) {
  //handle error - hopefully not with a console.log ;)
  console.log(e);
}
{% endhighlight %}

## Use **FIXME:** and **TODO:** comment to annotate problems

Prefixing your comments with **FIXME** or **TODO** helps other developers quickly understand if you're pointing out a problem that needs to be revisited, or if you're suggesting a solution to the problem that needs to be implemented.

* Use `// FIXME:` to annotate problems

{% highlight js %}
function Calculator() {

  // FIXME: shouldn't use a global here
  total = 0;

  return this;
}
{% endhighlight %}

* Use `// TODO:` to annotate solutions to problems

{% highlight js %} 
function Calculator() {

  // TODO: total should be configurable by an options param
  this.total = 0;

  return this;
}
{% endhighlight %}

## Whitespace rightway

* Use soft tabs set to 2 spaces

{% highlight js %}
// bad
function() {
∙∙∙∙var name;
}

// bad
function() {
∙var name;
}

// good
function() {
∙∙var name;
}
{% endhighlight %}

* Place 1 space before the leading brace.

{% highlight js %}
// bad
function test(){
  console.log('test');
}

// good
function test() {
  console.log('test');
}

// bad
dog.set('attr',{
  age: '1 year',
  breed: 'Bernese Mountain Dog'
});

// good
dog.set('attr', {
  age: '1 year',
  breed: 'Bernese Mountain Dog'
});
{% endhighlight %}

* Set off operators with spaces.

{% highlight js %}
// bad
var x=y+5;

// good
var x = y + 5;
{% endhighlight %}

* End files with a single newline character.

{% highlight js %}
// bad
(function(global) {
  // ...stuff...
})(this);

// bad
(function(global) {
  // ...stuff...
})(this);↵
↵

// good
(function(global) {
  // ...stuff...
})(this);↵
{% endhighlight %}

## Use lowerCamelCase for variables, properties and function names

Variables, properties and function names should use `lowerCamelCase`.  They
should also be descriptive. Single character variables and uncommon
abbreviations should generally be avoided.

*Right:*

{% highlight js %}
var adminUser = db.query('SELECT * FROM users ...');
{% endhighlight %}

*Wrong:*

{% highlight js %}
var admin_user = db.query('SELECT * FROM users ...');
{% endhighlight %}

## Use UpperCamelCase for class names

Class names should be capitalized using `UpperCamelCase`.

*Right:*

{% highlight js %}
function BankAccount() {
}
{% endhighlight %}

*Wrong:*

{% highlight js %}
function bank_Account() {
}
{% endhighlight %}

## Use UPPERCASE for Constants

Constants should be declared as regular variables or static class properties,
using all uppercase letters.

Node.js / V8 actually supports mozilla's [const][const] extension, but
unfortunately that cannot be applied to class members, nor is it part of any
ECMA standard.

*Right:*

{% highlight js %}
var SECOND = 1 * 1000;

function File() {
}
File.FULL_PERMISSIONS = 0777;
{% endhighlight %}

*Wrong:*

{% highlight js %}
const SECOND = 1 * 1000;

function File() {
}
File.fullPermissions = 0777;
{% endhighlight %}

[const]: https://developer.mozilla.org/en/JavaScript/Reference/Statements/const

## Object / Array creation

Use trailing commas and put *short* declarations on a single line. Only quote
keys when your interpreter complains:

*Right:*

{% highlight js %}
var a = ['hello', 'world'];
var b = {
  good: 'code',
  'is generally': 'pretty',
};
{% endhighlight %}

*Wrong:*

{% highlight js %}
var a = [
  'hello', 'world'
];
var b = {"good": 'code'
        , is generally: 'pretty'
        };
{% endhighlight %}

## Use the === operator

Programming is not about remembering [stupid rules][comparisonoperators]. Use
the triple equality operator as it will work just as expected.

*Right:*

{% highlight js %}
var a = 0;
if (a !== '') {
  console.log('winning');
}

{% endhighlight %}

*Wrong:*

{% highlight js %}
var a = 0;
if (a == '') {
  console.log('losing');
}
{% endhighlight %}

[comparisonoperators]: https://developer.mozilla.org/en/JavaScript/Reference/Operators/Comparison_Operators

## Use multi-line ternary operator

The ternary operator should not be used on a single line. Split it up into multiple lines instead.

*Right:*

{% highlight js %}
var foo = (a === b)
  ? 1
  : 2;
{% endhighlight %}

*Wrong:*

{% highlight js %}
var foo = (a === b) ? 1 : 2;
{% endhighlight %}

## Do not extend built-in prototypes

Do not extend the prototype of native JavaScript objects. Your future self will
be forever grateful.

*Right:*

{% highlight js %}
var a = [];
if (!a.length) {
  console.log('winning');
}
{% endhighlight %}

*Wrong:*

{% highlight js %}
Array.prototype.empty = function() {
  return !this.length;
}

var a = [];
if (a.empty()) {
  console.log('losing');
}
{% endhighlight %}

## Use descriptive conditions

Any non-trivial conditions should be assigned to a descriptively named variable or function:

*Right:*

{% highlight js %}
var isValidPassword = password.length >= 4 && /^(?=.*\d).{4,}$/.test(password);

if (isValidPassword) {
  console.log('winning');
}
{% endhighlight %}

*Wrong:*

{% highlight js %}
if (password.length >= 4 && /^(?=.*\d).{4,}$/.test(password)) {
  console.log('losing');
}
{% endhighlight %}

## Write small functions

Keep your functions short. A good function fits on a slide that the people in
the last row of a big room can comfortably read. So don't count on them having
perfect vision and limit yourself to ~15 lines of code per function.

## Return early from functions

To avoid deep nesting of if-statements, always return a function's value as early
as possible.

*Right:*

{% highlight js %}
function isPercentage(val) {
  if (val < 0) {
    return false;
  }

  if (val > 100) {
    return false;
  }

  return true;
}
{% endhighlight %}

*Wrong:*

{% highlight js %}
function isPercentage(val) {
  if (val >= 0) {
    if (val < 100) {
      return true;
    } else {
      return false;
    }
  } else {
    return false;
  }
}
{% endhighlight %}

Or for this particular example it may also be fine to shorten things even
further:

{% highlight js %}
function isPercentage(val) {
  var isInRange = (val >= 0 && val <= 100);
  return isInRange;
}
{% endhighlight %}

## Name your closures

Feel free to give your closures a name. It shows that you care about them, and
will produce better stack traces, heap and cpu profiles.

*Right:*

{% highlight js %}
req.on('end', function onEnd() {
  console.log('winning');
});
{% endhighlight %}

*Wrong:*

{% highlight js %}
req.on('end', function() {
  console.log('losing');
});
{% endhighlight %}

## No nested closures

Use closures, but don't nest them. Otherwise your code will become a mess.

*Right:*

{% highlight js %}
setTimeout(function() {
  client.connect(afterConnect);
}, 1000);

function afterConnect() {
  console.log('winning');
}
{% endhighlight %}

*Wrong:*

{% highlight js %}
setTimeout(function() {
  client.connect(function() {
    console.log('losing');
  });
}, 1000);
{% endhighlight %}

## Use slashes for comments

Use slashes for both single line and multi line comments. Try to write
comments that explain higher level mechanisms or clarify difficult
segments of your code. Don't use comments to restate trivial things.

*Right:*

{% highlight js %}
// 'ID_SOMETHING=VALUE' -> ['ID_SOMETHING=VALUE', 'SOMETHING', 'VALUE']
var matches = item.match(/ID_([^\n]+)=([^\n]+)/));

// This function has a nasty side effect where a failure to increment a
// redis counter used for statistics will cause an exception. This needs
// to be fixed in a later iteration.
function loadUser(id, cb) {
  // ...
}

var isSessionValid = (session.expires < Date.now());
if (isSessionValid) {
  // ...
}
{% endhighlight %}

*Wrong:*

{% highlight js %}
// Execute a regex
var matches = item.match(/ID_([^\n]+)=([^\n]+)/);

// Usage: loadUser(5, function() { ... })
function loadUser(id, cb) {
  // ...
}

// Check if the session is valid
var isSessionValid = (session.expires < Date.now());
// If the session is valid
if (isSessionValid) {
  // ...
}
{% endhighlight %}

## Object.freeze, Object.preventExtensions, Object.seal, with, eval

Crazy shit that you will probably never need. Stay away from it.

## Getters and setters

Do not use setters, they cause more problems for people who try to use your
software than they can solve.

Feel free to use getters that are free from [side effects][sideeffect], like
providing a length property for a collection class.

[sideeffect]: http://en.wikipedia.org/wiki/Side_effect_(computer_science)