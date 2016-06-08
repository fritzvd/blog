---
author: fritzvd
categories:
- development
- javascript
- node
- nodeconf15
date: 2015-06-22T14:20:37Z
guid: http://blog.technokrat.nl/?p=612
id: 612
title: Universal (Isomorphic) JavaScript and Modular UI @ nodeconf 2015
url: /2015/06/22/isomorphic-javascript-and-modular-ui-nodeconf-2015/
cover: https://farm4.staticflickr.com/3846/18687844349_4dcf82f7a3_q_d.jpg
---

N.B. This one of the first sessions held at nodeconf, everybody was still somewhat rusty.

Isomorphic JavaScript is the practice of using the same JavaScript code on the server and in the browser. In the session we talked about how to best implement this, and what to avoid. The naming is ridiculous, so let&#8217;s just use <a href="https://medium.com/@mjackson/universal-javascript-4761051b7ae9" target="_blank">Universal JavaScript</a>.

One of the first recommendations were to do static analysis. This goes through your code and finds dead dependencies or function that are never called. By using this you can eliminate redundancy in this way. Some modules that work great for this are <a href="https://twitter.com/substack" target="_blank">@substack&#8217;s</a> <a href="https://www.npmjs.com/package/detective" target="_blank">detective</a> or the module tree analysis by <a href="https://twitter.com/hughsk" target="_blank">@hughsk</a> called <a href="http://hughsk.io/disc/" target="_blank">disk</a> (looks good too!).

**UPDATE:**

Substack actually did a talk on Abstract Syntax Tree&#8217;s (which can be used to do static analysis) at <a href="https://jquerysf.com" target="_blank">jQuerySF</a>, which goes a bit more into detail on what you can do with AST&#8217;s and how Static Analysis works behind the scenes.



React got a lot of attention too. A small template rendering engine that let&#8217;s you render the page on the server, and with the same set of libraries render the changes on the front-end. So the page is fully loaded when you first land on the page, in stead of the startup time that&#8217;s required for full-fledged MVC(-likes) such as: AngularJS, Ember and Backbone. React&#8217;s server side rendering here is the one thing that really stands out, together with the speed and the small size of the library. Most people really seem to be fond of this approach (after dealing with the ugliness which is JSX).

According to substack, we shouldn&#8217;t use big shims, we shouldn&#8217;t use frameworks. Because it will break stuff, or come back to haunt you. Especially if you&#8217;re trying to run Universal JS. We should create small modules that uses CommonJS&#8217; `module.exports`.

This kind of moved on to the discussion of Modular UI which was another topic. The gist of this session was to make modules that expose css and assets through inline css or conditional building. A well known implementation doing UI in this way is the <a href="https://www.polymer-project.org/1.0/docs/devguide/feature-overview.html" target="_blank">Polymer Project</a>. Every component is a module that doesn&#8217;t have to be a part of the rest of the project. To include a small piece, you just: `npm install --save my-special-module`.

See <a href="https://twitter.com/davidguttman" target="_blank">David Guttman&#8217;s</a> <a href="https://github.com/davidguttman/cssify" target="_blank">cssify</a> for a way to include the required css files with browserify.

The rest of my notes say:

  * Distribution.
  * UMD.

So if anyone feels like filling me on on what this meant, that would be grand. <img src="http://blog.technokrat.nl/wp-includes/images/smilies/simple-smile.png" alt=":)" class="wp-smiley" style="height: 1em; max-height: 1em;" />

<a href="https://www.flickr.com/photos/matthewbergman/18687844349/in/album-72157654202715069/" target="_blank">Cover photo by Matthew Bergman</a>
