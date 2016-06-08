---
author: fritzvd
categories:
- javascript
- node
date: 2014-09-13T11:11:52Z
excerpt: Streams, pipes, data channels, crazy a/b testing and performance
guid: http://blog.technokrat.nl/?p=552
id: 552
tags:
- frontend
- javascript
- node
- nodeconf
- nodeconfeu
title: Front end track at nodeconf.eu
url: /2014/09/13/front-end-track-at-nodeconf-eu/
---

The frontend track featured some very different talks , ranging from performance to a/b testing. In that sense it was a bit different from the <a href="http://blog.technokrat.nl/2014/09/12/microservices-track-summary-nodeconfeu/" title="Microservices Track summary #nodeconfeu" target="_blank">microservices track</a>, because it was less of a &#8216;one story&#8217; thing.

**Scaling A/B testing at Netflix &#8211; <a href="https://twitter.com/stinkydofu" title="@stinkydofu" target="_blank">Alex Liu</a>**
  
Netflix takes a/b testing to the next level, where they break up the UI in little pieces and run a/b tests on all of them at once. One user can be in several a/b tests at one point in time. They do hundreds of these tests a year, which means they have to deliver 2.5 million unique packages a week (!!!!!!!). This in itself is astounding. 

The problem with these packages is conditional packages. So for example search is updated and needs some old dependencies and some old dependencies (see slide below).
  


To build this to scale you don&#8217;t want to have someone picking the correct packages by hand. For that they wrote a node module that looks at the docstring of a function/file. Which can have a ruleset explaining when it should or should not be included. In the build process the packages are selected that should be part of it and which should not. With every request to the node server that runs the assets, the registry is consulted, the rules are applied and packaged and cached and served from a CDN for the next person in the same a/b test group.

Fail fast, move faster (to improve that is, your goal should not be to fail).

**Fullstack through microservices &#8211; <a href="https://twitter.com/matteocollina" title="@matteocollina" target="_blank">Matteo Collina</a>**

Matteo talked about using data channels and RPC&#8217;s (remote procedure calls) from the back end to the frontend. Using data streams in stead of request/response patterns. In stead of returning a delimited block of data you can return a channel. This makes it possible to receive and unpack or send and connect binary data directly to or from the frontend. Anything that is serializable to JSON, Node.js binary streams or even other channels can all be sent through this mechanism.

So to have a framework of these types of microservices they created Graft. 

_Update: oh and he used this really cool cheap sensor to do his talk: <a href="https://estore.ti.com/CC2541DK-SENSOR-CC2541-SensorTag-Development-Kit-P3192.aspx" title="SensorTag" target="_blank">SensorTag</a>_

**Building high quality services at Uber &#8211; <a href="https://twitter.com/raynos" title="@raynos" target="_blank">Jake Verbaten</a>**
  
Raynos started with a funny story where his first day was to build a proxy service. Oh and it will be deployed to about 50 machines. Oh and they can&#8217;t go down ever. 

Of course when you make something, you have to go over it again to &#8220;productionize&#8221; it. In order to do this, he showed some tools they use at Uber to get this going.

The one that stood out the most was _potter_ (which they&#8217;re still &#8220;open-sourcifying&#8221;). It basically sets up a skeleton (or scaffolds) for your project, starts a github repo, and registers it at your CI server (i.e. travis, jenkins, wha-evah), starts logging to sentry and graphite.

**Demystifying v8 and javascript performance &#8211; <a href="https://twitter.com/thlorenz" title="@thlorenz" target="_blank">Thorsten Lorentz</a>**
  
The engine which is used for node.js is the same one as is used for Chrome/Chromium project: V8. Therefore similar problems that arise with node will also occur in the browser. Which means that performancewise you can apply the same principles. 

This is the talk that had me looking up lots of things in the end, so it at least was great food for thought. 

One of the easiest performance gains you can easily apply is to be clear about your intentions to the browser/v8 engine. Meaning you don&#8217;t start by declaring an empty list if you are then going to fill it up with a number of different types. Usually you should stay away from different types in one array altogether, but performance will severely drop if you are not being upfront to the interpreter.
  
Example:
  


He also went into great detail about how you don&#8217;t want to keep on changing an Object structure after construction, because at one point v8 will give up and fall-back to the unoptimizable slow HashTable structure. But rather than I try to reproduce this look at this blog post: <a href="http://jayconrod.com/posts/52/a-tour-of-v8-object-representation" title="a-tour-of-v8-object-representation" target="_blank">A tour of v8 object representation</a>

<a href="http://thlorenz.github.io/talks/demystifying-v8/talk.pdf" title="slides" target="_blank">and the slides themselves</a>

**Final thoughts**
  
<a href="https://twitter.com/davidmarkclem" title="@davidmarkclem" target="_blank">David Clements</a> did a workshop on working with streams and data from front end to the backend (and vice versa) which covered lots of ground similar to what Matteo squeezed into 20 min. Check it out here: <a href="https://www.dropbox.com/sh/9ra61cq9qgpxyx0/AACXumrkWesFs7jrhI4uUEula/slides.pdf?dl=0" title="back to the frontend" target="_blank">Slides</a>