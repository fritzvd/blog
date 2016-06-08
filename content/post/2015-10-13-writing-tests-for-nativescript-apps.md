---
author: fritzvd
categories:
- Uncategorized
date: 2015-10-13T06:49:23Z
guid: http://blog.technokrat.nl/?p=668
id: 668
title: Writing Tests for NativeScript apps
url: /2015/10/13/writing-tests-for-nativescript-apps/
cover: https://farm4.staticflickr.com/3236/3134743730_15e066077d_q_d.jpg
---

This has been bugging me for a while. While working on my business logic and REST API connection in my NativeScript project, I couldn&#8217;t write tests because requiring the tns-core-modules broke the test.

<a href="https://www.nativescript.org/" target="_blank">NativeScript</a> is a library with tooling to create iOS and Android apps in JavaScript. And it works smoothly. However at the moment the docs aren&#8217;t always complete. Anyways, building and deploying an app on a mobile device (or emulator) takes somewhere in the range of a minute or so on a fast machine.

That doesn&#8217;t really work if you&#8217;re not sure if your logic makes sense.

In comes `<a href="http://npmjs.com/package/proxyquire" target="_blank">proxyquire</a>`. Install proxyquire:

<pre><code class="syntax bash">npm install --save-dev proxyquire
</code></pre>

Then make sure you stub the package you want to be stubbed, with @noCallThru.

Example:



So now you can setup mocha for example to work with the app.

<pre><code class="syntax bash">npm install --save-dev mocha
</code></pre>

Edit your package.json so your npm scripts reads:

<pre><code class="syntax javascript">"scripts": {
    "test": "mocha tests/*",
    "start": "node index.js"
  },
</code></pre>

And go ahead and run `npm test`

<small>Cover image courtesy of Willie Hardin: https://www.flickr.com/photos/14934865@N07/3134743730/</small>
