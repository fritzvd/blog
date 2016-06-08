---
author: fritzvd
categories:
- javascript
- node
date: 2014-09-15T11:53:39Z
guid: http://blog.technokrat.nl/?p=578
id: 578
tags:
- javascript
- mad science
- node
- nodeconf
- nodeconfeu
title: Mad Science Act &#8211; part 1@ nodeconf.eu
url: /2014/09/15/mad-science-act-part-1-nodeconf-eu/
---

The Mad Science Act, was something completely different. It featured many topics and some of the most creative and prolific npmjs.org authors. It was a bit mad, so I&#8217;ll try to make it as coherent as I understood it. I have split up the post in 2 parts. It would be too much put into one.

**Professor <a title="substack" href="https://twitter.com/substack" target="_blank">Substack</a> &#8211; Mad Science intro.**
  
When you start out creating (npm) modules you realize there is a great shortage of modules. And you need to create much more. A lot of tools are already readily available and they one thing and try to do it right. The tools are small concise and are encapsulated, they seperate concern and are in that sense: &#8216;orthogonal&#8217;.

<div style="width: 1450px" class="wp-caption alignnone">
  <a href="https://github.com/substack/nodeconf.eu-2014"><img class="" src="https://raw.githubusercontent.com/substack/nodeconf.eu-2014/master/images/060_orthogonal.png" alt="" width="1440" height="1080" /></a>
  
  <p class="wp-caption-text">
    orthogonal &#8211; substack
  </p>
</div>

Still with all the tools that are readily available, they don&#8217;t cover all use cases. Besides focusing on test coverage, we should take into account solving more and more use cases. So go dumpster diving for stuff that can output other stuff by multiplexing data streams. For example with <a title="dataplex" href="https://github.com/substack/dataplex" target="_blank">dataplex</a>. It helps you to capture and organize multiple streams over a single stream. Conveying it over e.g. tcp or web socket connections.

_this is where it all went fuzzy_
  
Then Substack did some live code demo&#8217;s, to create a quick webserver, continuous integration server etc. with some readily available tools and piping the data to dataplex. There is a pretty good example on the <a title="dataplex" href="https://github.com/substack/dataplex" target="_blank">&#8216;dataplex&#8217; github page</a>

**<a title="feross" href="https://twitter.com/feross" target="_blank">Feross</a> &#8211; webtorrent**
  
This talk portrayed a powerful implementation of webrtc. Using WebRTC as an alternative skype, <a title="hello chrome it's firefox calling" href="https://hacks.mozilla.org/2013/02/hello-chrome-its-firefox-calling/" target="_blank">is something we&#8217;ve seen before</a>. And it&#8217;s great, but there is also the <a title="datachannels on html5rocks" href="http://www.html5rocks.com/en/tutorials/webrtc/datachannels/" target="_blank">DataChannel</a>. An api that delivers a peer-to-peer data connection <a title="webrtc infrastructure" href="http://www.html5rocks.com/en/tutorials/webrtc/infrastructure/" target="_blank">&#8216;without a server&#8217;</a>.

A peer-to-peer data connection of course sounds but a step away from things like the beautiful BitTorrent protocol. In comes <a title="webtorrent" href="https://github.com/feross/webtorrent" target="_blank">webtorrent</a>. A tool created to use the bittorrent protocol for decompartmentalizing files with a verification hash, and start sharing these small parts of a file, so once a person has that small bit, it can already share that part. Only the catch is that it can do this over the web. The webtorrent client runs in any webRTC (datachannel) compatible browser. For now that means Firefox and Chrome.
  
An example of this can be found on <a title="instant.io" href="http://instant.io/" target="_blank">instant.io</a> (send me a message if you want to try it ☺ <a title="@fritzvd" href="https://twitter.com/fritzvd" target="_blank">twitter</a>).
  
Because bittorrent works over TCP/UDP webtorrent and bittorrent can&#8217;t connect (yet) directly. But they need hybrid clients in between. So Feross is working on a command line webtorrent client, that functions as a &#8216;hybrid&#8217; client.

The awesomerestest was a live demo of a <a title="webrtc-whiteboard" href="https://github.com/feross/webrtc-whiteboard" target="_blank">webrtc-whiteboard</a> which can also be <a title="whiteboard" href="http://instant.io:8080/" target="_blank">tested live</a>. It&#8217;s still very PoC-y though. But it was great to see it working these small bits and pieces that make up webtorrent and seeing it being used by people in the audience as well, for sharing cat video&#8217;s and images:

<blockquote class="twitter-tweet" lang="en">
  <p>
    <a href="https://twitter.com/feross">@feross</a> doing webrtc mad science <a href="https://twitter.com/hashtag/nodeconfeu?src=hash">#nodeconfeu</a> <a href="http://t.co/Kxf1BL4qd9">pic.twitter.com/Kxf1BL4qd9</a>
  </p>
  
  <p>
    — Magnus (@ralphtheninja) <a href="https://twitter.com/ralphtheninja/status/509649443097169920">September 10, 2014</a>
  </p>
</blockquote>



Go over and help Feross. His project is now <a title="OPEN Open Source" href="http://blog.technokrat.nl/2014/09/15/open-open-source/" target="_blank">&#8220;open open source&#8221;.</a>