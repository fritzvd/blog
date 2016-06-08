---
author: fritzvd
categories:
- development
- javascript
date: 2013-06-18T11:48:43Z
guid: http://blog.technokrat.nl/?p=440
id: 440
tags:
- angular
- development
- favorites
- favourites
- javascript
title: Angular JS Favourites/Favorites &#8211; Directives &#8211;  jQuery UI Slider
url: /2013/06/18/angular-js-favorites-directives-jquery-ui-slider/
---

Last time I wrote something about something very simple, but something I really enjoy. Conditional classes and inline event handlers. It&#8217;s not a very difficult or complex feature. But I did not find a lot of writing about it. And also it saved me loads of jQuery statements that you don&#8217;t want in a controller, but in the UI.

### Next up: Directives.

<a title="Angular Docs on Directives" href="http://docs.angularjs.org/guide/directive" target="_blank">Directives</a> are pret-ty awesomevilles. For the &#8220;stop/play video player like&#8221;-thing we are building, we would like to have a timeline or time slider, to go back to a previous images. Normally this would be a jQuery (jQuery UI) call like so:

<pre><code class="syntax html">&lt;div id="id-of-div-or-wha-evah"&gt;&lt;/div&gt;
</code></pre>

<pre><code class="javascript syntax">$('#id-of-div-or-wha-evah').slider()</code></pre>

Which would be fine if you need only one of these, or if you would have a small app. With an Angular Directive it becomes a bit more complex, but also a lot more useful. Our product is a <a title="3di" href="http://www.3di.nu" target="_blank">groundbreaking flooding model</a>. Basically you can run a super fast flooding simulation in the cloud and look at the results on-the-fly in your browser. With every simulation step the complete timeline becomes longer, thus we need a timeline that can listen to other states and messages in our application. Because all the states and messages are already in the app, I don&#8217;t want to jQuery my way out of this one.

So I created the following HTML component and angular directive.

If you&#8217;re to lazy to look up the <a title="Angular Docs on Directives" href="http://docs.angularjs.org/guide/directive" target="_blank">docs</a>, I&#8217;ll give you some pointers. The most important thing to notice here is that the directive and the html element correspond because of the title. The html tag: _<jq-schlider>_ is recognized by the _jqSchlider_ directive defined in angular because of the _restrict: &#8216;E&#8217;_ line. The _E_ stands for element but can also be replaced by something else (look in the docs) if that has your fancy.

The HTML attributes max and at are picked up by the directive as variables. The values come from the Controller in which the jqSchlider will be inserted.

The fiddle below is a working example:
  


Get this btw it&#8217;s great: