---
author: fritzvd
categories:
- javascript
- node
date: 2014-09-12T11:17:59Z
excerpt: Microservices, small building blocks that do one thing.
guid: http://blog.technokrat.nl/?p=550
id: 550
tags:
- javascript
- microservices
- node
- nodeconf
- nodeconfeu
title: 'Microservices Track summary #nodeconfeu'
url: /2014/09/12/microservices-track-summary-nodeconfeu/
---

The microservices track came down to most speakers saying things more or less in similar vain, each talk having its own emphasis. <a href="https://twitter.com/rjrodger" title="rjrodger" target="_blank">Richard Rodger</a> opened up and basically laid the groundwork for the microservices bit together with the <a href="https://twitter.com/fgeorge52" title="fgeorge52" target="_blank">Fred George</a> talk.

After hearing the talks I&#8217;d define microservices as small blocks that can run independently and do one thing, along the Unix philosophy. Making building blocks in stead of one big application that does everything. Now instead of including this one small thing in the rest of your app, you run this as a single thing which returns results based on messaging.

Your services will be fairly stupid as in that they will not know about the other services. So in order to communicate with each other you have the services talk to a message bus.

What this enables is having:

  * a naturally scalable application
  * naturally scalable teams (as you don&#8217;t need to know about the whole system)
  * polyglot applications without it becoming a problem

The nice thing about developing an application as a combination of microservices is it enables seperate small deployments. Versions of software can be bumped seperately and released seperately without the whole server having to suffer.

Now the implementation and how different microservices work together differs amongst the various speakers.

And of course different problems arise you now have lots of apps and servers to maintain, and you have to present this whole bunch of services as one application which feels like a wholistic thing to the user. According to <a href="https://twitter.com/dglozic" title="dglozic" target="_blank">Dejan Glozic</a> this could be solved with what he called: local clustering. <a href="https://twitter.com/clifcunn" title="clifcunn" target="_blank">Clifton Cunningham</a> put forward a few solutions for this: client side assembly, front end server, server side includes or edge side include. Or of course: build it yourself → <a href="https://www.npmjs.org/package/compoxure" title="compoxure" target="_blank">Compoxure</a>.
  
In this scenario every service hosts and returns it&#8217;s own rendered html (or json if you request that format). If a service dies, the cache will run the last known good html or the html renders a default.
  
For the static files part it&#8217;s similar. Every service knows which static files it needs and rakes them together with a tool called: <a href="https://www.npmjs.org/package/bosco" title="bosco" target="_blank">Bosco</a>.

The company Richard Rodger co-founded nearForm built a solution for the local clustering problem in their microservices framework <a href="https://www.npmjs.org/package/seneca" title="seneca" target="_blank">Seneca</a>, their objective is best explained in the project website.

Programming anarchist Fred George threw his own version in the mix, where he said all services receive all messages all the time. You can then categorize the message in his metaphor of Rapids, Rivers and Ponds. The rapids are the streams with all the messages. The rivers the themed events and the ponds things like state/history.
  
A service should be so seperate, you should even have all the microservices have their own persistence layer. If a service has 2 jobs, make 2 services out of it.

Microservices FTW.