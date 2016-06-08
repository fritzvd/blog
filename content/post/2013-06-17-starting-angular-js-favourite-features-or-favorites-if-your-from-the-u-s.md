---
author: fritzvd
categories:
- development
- javascript
date: 2013-06-17T17:22:19Z
guid: http://blog.technokrat.nl/?p=439
id: 439
tags:
- angular
- development
- favorites
- favourites
- javascript
title: Angular JS Favourites/Favorites &#8211; Conditional CSS classes
url: /2013/06/17/starting-angular-js-favourite-features-or-favorites-if-your-from-the-u-s/
---

Last few weeks at work I have been trying out Angular JS. First of all, because it is fun and useful to try out new stuff. Secondly because after working with <a title="marionette" href="http://marionettejs.com/" target="_blank">Backbone/Marionette</a> for a few months some things felt that they could&#8217;ve been done better. So whilst working on a big Backbone/Marionette <a title="ddsc" href="http://github.com/ddsc/webclient" target="_blank">project</a> I started looking at Angular a bit.

I&#8217;ll just show you some of my favourite features. We are building an app that needs to play, stop, pause etc much like a video player. But we need to do quite a bit more than that. I&#8217;ll highlight two features that really helped out clear out some old jQuery blah blah. Maybe I&#8217;ll write some more on my favourites coming week.

### **Conditional CSS classes:**

One thing that I kept running into is having to decide when to use a jQuery handler or a Backbone built-in function to toggle a CSS class. This sounds trivial, and maybe it is, but this is such a common feature in a interactive client, that it is a relief to see it handled nicely.

### **Inline coupling of DOM element and javascript function:**

I know, I know this is done in almost any MVC framework. But I just like the way Angular has set this up. Just add HTML attribute `ng-click="nameoffunction()"` and the `$scope.nameoffunction` function responds to this. Example below clarifies both Conditional CSS classes and click-handler.

Example play and stop button.:

<pre><code class="syntax html">&lt;div ng-controller="RemoteControl"&gt; 
  &lt;a id="btn-play" class="btn" ng-class="{active: isPlaying}" ng-click="play()"&gt;
    &lt;i class="icon-play"&gt;&lt;/i&gt;
  &lt;/a&gt;
&lt;/div&gt;
</code></pre>

<pre><code class="syntax javascript">app.controller("RemoteControl", ["$scope"], function($scope){
   $scope.isPlaying = false;

   $scope.play = function() {
      if ($scope.isPlaying) {
        // if already playing turn it off.
        $scope.isPlaying = false;
      } else {
         // do stuff involved with play
         // switch isPlaying to true
         $scope.isPlaying = true;
      }
   }
}]);
</code></pre>

Next week I&#8217;ll make some time to discuss Directives.
