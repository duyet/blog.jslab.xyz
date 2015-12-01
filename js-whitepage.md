---
layout: page
title: Javascript Whitepage
permalink: /white-page/
---

*(this page is in process, please pull request to contribute for this page)*

# 1.1 History of JavaScript
JavaScript was developed by Brendan Eich under the name Mocha as an enhancement to
the Netscape browser and renamed to LiveScript at its beta release in 1995. It was later
renamed to JavaScript as a marketing move and as such was officially released with
Netscape 2.0 in March 1996. Microsoft implemented its own version of the language
called JScript. The two languages were standardized under the name ECMA-262
(ECMAScript) when European Computer Manufacturers Association (ECMA) approved
Netscape’s application in 1996. Since then ECMA has published 5 versions of the
specifications with the latest version - 5.1 being released in June 2011. [5]

While the language has an official standard in the name of *ECMAScript* it is still
developed separately by Microsoft under the name of JScript. There are other
implementations of the ECMAScript standard and different engines that run them. Of these
JScript and JavaScript are often confused with one another and produce many problems on
the browser side. Although outdated, the mapping of different JavaScript implementations
and connections done in 2007 [Appendix 1] gives an idea of how varied the landscape is.
On the server side the first implementation of JavaScript was by Netscape in 1996.
Netscape was planning to introduce a browser written only in Java and thus needed a Java
implementation of JavaScript – project „Javagator“. Although the project was terminated,
its subproject „Rhino“ remained [6]. Rhino passed on to mozilla.org project (later to
become Mozilla Foundation) in 1998 and has been under its development since. It was not
accepted by a wider user base and thus has had a slow progress. The current version
conforms to ECMAScript 3, which is over a decade old. [7]

In 2006 Google was working on entering the browser market and needed a JavaScript
engine to run in their browser. Development started on a JavaScript engine named V8 [8].
V8 compiles JavaScript into native machine code before executing it to increase the
performance. The engine itself is developed to be embeddable, allowing it to be used in
10 any environment supporting C++. This appealed to Ryan Dahl who adopted V8 in his
project to build a new application platform in the beginning of 2009. By the end of 2009
Node.js was in version 0.1.24 and still in its infancy. Over the next years it gained
popularity and by 2012 May it is in version 0.6.16 and shows no signs of slowing down.
[9]

JavaScript has had a chaotic development due to its multi-faced nature which held back the
adoption of new features for quite some time. It started out as a simple scripting language
meant to provide some interactivity to static HTML web pages. By now it has grown into a
powerful programming language which ships on every desktop computer. This simple
beginning accounts for the lack of built in security in JavaScript and causes some specific
problems when developing applications on Node.js.

# References
[1]: "Welcome! - The Apache HTTP Server Project," [WWW]: http://httpd.apache.org/.
(24.05.2012).
[2]: "Node.js," [WWW]: http://nodejs.org/. (22.05.2012).
[3]: "Google- Company," [WWW]: http://www.google.com/about/company/. (22.05.2012).
[4]: "About Microsoft: Your Potential. Our Passion.," [WWW]:
http://www.microsoft.com/about/en/us/default.aspx. (22.05.2012).
[5]: A. White, JavaScript Programmer's Reference, John Wiley & Sons, 2010.
[6]: "Rhino History," [WWW]: http://www.mozilla.org/rhino/history.html. (22.05.2012).
[7]: "JavaScript Overview," [WWW]: http://www.mozilla.org/rhino/overview.html.
(22.05.2012).
[8]: Google Inc, "v8 - V8 JavaScript engine," [WWW]: http://code.google.com/p/v8/.
(22.05.2012).
[9]: "Node.js ChangeLog," [WWW]: http://nodejs.org/changelog.html. (22.05.2012).
[10]: C. Severance, "Java Script: Designing a Language in 10 Days," Computer, pp. 7-8,
February 2012.
[11]: J. Resig, "Chapter 2 - Object Oriented Javascript," in Pro JavaScript Techniques,
2006, pp. 25-26.
[12]: ECMA International, "ECMA International," [WWW]: http://www.ecmainternational.org/publications/files/ECMA-ST/Ecma-262.pdf.
(22.05.2012).
[13]: M. W. Tom Hughes-Croucher, "A Very Brief Introduction to Node.js," in Node: Up
and Running: Scalable Server-Side Code with JavaScript, 2012, pp. 3-4.
[14]: "npm - Node Package Manager," [WWW]: http://npmjs.org. (22.05.2012).
[15]: "LinkedIn Mobile | LinkedIn," [WWW]: http://www.linkedin.com/static?key=mobile.
(23.05.2012).
[16]: "Windows Azure: Cloud Computing | Cloud Services | Cloud Application
Development," [WWW]: http://www.windowsazure.com/en-us/. (23.05.2012).
[17]: S. T. a. S. Vinoski, "Node.js: Using JavaScript to Build High-Performance Network
Programs," Internet Computing, vol. 14, no. 6, pp. 80-83, 2010.
[18]: "Aaronontheweb | Intro to Node.JS for .NET Developers," [WWW]: 
54
http://www.aaronstannard.com/post/2011/12/14/Intro-to-NodeJS-for-NETDevelopers.aspx.
(22.05.2012).
[19]: "Introduction to Node.js with Ryan Dahl - YouTube," [WWW]:
http://www.youtube.com/watch?v=jo_B4LTHi3I. (22.05.2012).
[20]: "ab - Apache HTTP server benchmarking tool," [WWW]:
http://httpd.apache.org/docs/2.0/programs/ab.html. (22.05.2012).
[21]: "Slowloris HTTP DoS," [WWW]: http://ha.ckers.org/slowloris/. (22.05.2012).
[22]: "Nginx - Main," [WWW]: http://wiki.nginx.org/Main. (23.05.2012).
[23]: "lighttpd fly light," [WWW]: http://www.lighttpd.net/. (23.05.2012).
[24]: "Express - node web framework," [WWW]: http://expressjs.com/. (22.05.2012).
[25]: "Jade - Template engine," [WWW]: http://jade-lang.com/. (22.05.2012).
[26]: "Connect - High quality middleware for node.js," [WWW]:
http://www.senchalabs.org/connect/. (22.05.2012).
[27]: "28c3: Effective Denial of Service attacks against web application platforms,"
[WWW]: http://www.youtube.com/watch?v=R2Cq3CLI6H8. (23.05.2012).
[28]: "NPM - README," [WWW]: http://npmjs.org/doc/README.html. (23.05.2012).
[29]: "CommonJS effort sets JavaScript on path for world domination | Ars Technica,"
[WWW]: http://arstechnica.com/business/2009/12/commonjs-effort-sets-javascript-onpath-for-world-domination/.
(23.05.2012).
[30]: B. Sullivan, "Regular Expression Denial of Service Attacks and Defenses," MSDN
Magazine, vol. 25, no. 5, pp. 82-85, 2010.
[31]: "NPM - scripts," [WWW]: http://npmjs.org/doc/scripts.html. (23.05.2012).
[32]: "Classes.Big Number - JSFromHell.com: JavaScript Repository," [WWW]:
http://jsfromhell.com/classes/bignumber. (23.05.2012).
[33]: "nodejitsu/forever," [WWW]: https://github.com/nodejitsu/forever/. (23.05.2012).
[34]: "Ryan Dahl - History of Node.js - YouTube," [WWW]:
http://www.youtube.com/watch?v=SAc0vQCC6UQ#!. (23.05.2012).
