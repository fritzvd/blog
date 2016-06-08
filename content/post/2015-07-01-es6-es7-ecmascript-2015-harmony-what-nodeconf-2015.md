---
author: fritzvd
categories:
- development
- javascript
- node
- nodeconf15
date: 2015-07-01T07:35:35Z
guid: http://blog.technokrat.nl/?p=647
id: 647
title: ES6 + ES7, EcmaScript 2015 -- Harmony .. WHAT? @ nodeconf 2015
url: /2015/07/01/es6-es7-ecmascript-2015-harmony-what-nodeconf-2015/
cover: https://farm4.staticflickr.com/3810/18686339600_4a69372c14_q_d.jpg
---

### JavaScript gets a new version, what now

Languages are never done. They evolve over time and are supplemented with new words every month, new phrases every year and acquires (minor) grammar changes every decade. This true for speaking languages as well as for programming languages.

The past year there has been a lot of talk about EcmaScript 6 (a.k.a. ES Harmony, or lately ES2015, which is the silliest name of all). A set of features that is coming, or has already landed for JavaScript. ES6 is nothing more than a specification of features according to <a href="https://twitter.com/mikeal" target="_blank">Mikeal Rogers</a>. A specification of features that have been designed, but are not certain to land in the coming years. Some of them are just syntactic sugar (classes,9 , that don&#8217;t add anything new. Some are hurting performance and some are just plain great.

In the node community there has been some commotion surrounding ES6 because most of the features were suddenly being implemented in a fork of node called &#8220;io.js&#8221;. The temporary fork and squabble that is/has been (depending on when you read this) [&#8220;io.js](iojs.org)&#8221; was mainly to move node forward and out of a corporate governance model to a more open model. But you should just <a href="http://blog.izs.me/post/104685388058/io-js" target="_blank">read</a> <a href="http://www.wired.com/2014/12/io-js/" target="_blank">some</a> <a href="http://readwrite.com/2015/02/27/node-js-io-js-reconciliation-near" target="_blank">article</a> <a href="http://venturebeat.com/2015/05/13/node-project-spinoff-io-js-is-moving-to-the-node-js-foundation-with-a-merge-in-progress/" target="_blank">explaining</a> <a href="http://www.infoworld.com/article/2855057/application-development/why-iojs-decided-to-fork-nodejs.html" target="_blank">that</a>.

If you want to play around with these features, you either have to wait for some of the features to be implemented (in browsers and node.js alike), or you need a transpiler or polyfill framework, for backwards compatibility or even to run it because no one supports it yet&#8230; Most people are using <a href="https://babeljs.io/docs/learn-es2015/" target="_blank">Babel</a> which has a very decent set of docs and examples and transpiles your code back to ES5.

The thing that excites me most is the native promise implementation and the generators.

Then some people were really enthusiastic about an ES7 proposal for asynchronous functions: `async`. If a function is async, you just &#8220;tell&#8221; the VM by doing this (example taken from the <a href="https://github.com/lukehoban/ecmascript-asyncawait" target="_blank">async proposal</a>):

<pre><code class="syntax javascript">async function getData() {
  var items = await fetchAsync('http://example.com/users');
  return await* items.map(async(item) =&gt; {
    return {
      title: item.title,
      img: (await fetchAsync(item.userDataUrl)).img
    }
  });
}
</code></pre>

Take note of the `async` and the `await` keywords.

One of the <a href="https://github.com/DJCordhose/ecmascript-2015-iojs" target="_blank">workshops</a> at nodeconf was also about ES2015. It gives an overview of most features and you can play with the examples.

<a href="https://www.flickr.com/photos/matthewbergman/18686339600/in/album-72157654202715069/" target="_blank">Cover photo by Matthew Bergman</a>
