---
author: fritzvd
categories:
- development
- game
date: 2014-03-04T14:34:54Z
guid: http://blog.technokrat.nl/?p=522
id: 522
tags:
- emitter
- game development
- haxepunk
- particle
title: Particle Emitter in HaxePunk
url: /2014/03/04/particle-emitter-in-haxepunk/
---

For some this will be a trivial example. For me this took a bit longer than I suspected.

This small example will produce this:
  


If you&#8217;re planning on making an awesome game you probably want a particle emitter. because.. well look at it.

What I did is I started a haxepunk project:
  
`For some this will be a trivial example. For me this took a bit longer than I suspected.

This small example will produce this:
  


If you&#8217;re planning on making an awesome game you probably want a particle emitter. because.. well look at it.

What I did is I started a haxepunk project:
  
` 

And added a file: <a href="https://github.com/fritzvd/haxepunk-emitter-example/blob/master/src/Explosion.hx" title="Explosion.hx" target="_blank">Explosion.hx</a>
  
The Emitter is also a type of Entity, and also needs a graphic. It looks like this:

<pre><code class="syntax actionscript">import com.haxepunk.graphics.Emitter;
import com.haxepunk.utils.Ease;
import com.haxepunk.Entity;

class Explosion extends Entity
{
	private var _emitter:Emitter;

	public function new()
	{
		super(x, y);
        _emitter = new Emitter("graphics/particle.png", 4, 4);
        _emitter.newType("explode", [0]);
        _emitter.setMotion("explode",  		// name
		        	0, 				// angle
		        	100, 			// distance
		        	2, 				// duration
		        	360, 			// ? angle range
		        	-40, 			// ? distance range
		        	1, 				// ? Duration range
		        	Ease.quadOut	// ? Easing	
		        	);
        _emitter.setAlpha("explode", 20, 0.1);
        _emitter.setGravity("explode", 5, 1);
        graphic = _emitter;
        layer = -1;
	}

	public function explode(x:Float, y:Float)
	{
		for (i in 0...20)
		{
			_emitter.emit("explode", x, y);
		}
	}


}
</code></pre>

Then you can add the Emitter to your current scene like in my <a href="https://github.com/fritzvd/haxepunk-emitter-example/blob/master/src/MainScene.hx" title="MainScene.hx" target="_blank">MainScene.hx</a>
  
It looks like this:

<pre><code class="syntax actionscript">import com.haxepunk.Scene;
import Explosion;

class MainScene extends Scene
{
	private var explosion:Explosion;

	public override function begin()
	{
		explosion = new Explosion();
		add(explosion);
	}

	public override function update()
	{
        super.update();
        explosion.explode(230, 240);
	}
}
</code></pre>

Now run
  
`lime test neko`
  
And you should see something similar to the emitter above.

You can checkout my <a href="https://github.com/fritzvd/haxepunk-emitter-example" title="haxepunk-emitter-example" target="_blank">repo</a> and run it to play around with it.

I ran into this error below. It meant my sprite was too small. It took me a long time to realize that.
  
``For some this will be a trivial example. For me this took a bit longer than I suspected.

This small example will produce this:
  


If you&#8217;re planning on making an awesome game you probably want a particle emitter. because.. well look at it.

What I did is I started a haxepunk project:
  
`For some this will be a trivial example. For me this took a bit longer than I suspected.

This small example will produce this:
  


If you&#8217;re planning on making an awesome game you probably want a particle emitter. because.. well look at it.

What I did is I started a haxepunk project:
  
` 

And added a file: <a href="https://github.com/fritzvd/haxepunk-emitter-example/blob/master/src/Explosion.hx" title="Explosion.hx" target="_blank">Explosion.hx</a>
  
The Emitter is also a type of Entity, and also needs a graphic. It looks like this:

<pre><code class="syntax actionscript">import com.haxepunk.graphics.Emitter;
import com.haxepunk.utils.Ease;
import com.haxepunk.Entity;

class Explosion extends Entity
{
	private var _emitter:Emitter;

	public function new()
	{
		super(x, y);
        _emitter = new Emitter("graphics/particle.png", 4, 4);
        _emitter.newType("explode", [0]);
        _emitter.setMotion("explode",  		// name
		        	0, 				// angle
		        	100, 			// distance
		        	2, 				// duration
		        	360, 			// ? angle range
		        	-40, 			// ? distance range
		        	1, 				// ? Duration range
		        	Ease.quadOut	// ? Easing	
		        	);
        _emitter.setAlpha("explode", 20, 0.1);
        _emitter.setGravity("explode", 5, 1);
        graphic = _emitter;
        layer = -1;
	}

	public function explode(x:Float, y:Float)
	{
		for (i in 0...20)
		{
			_emitter.emit("explode", x, y);
		}
	}


}
</code></pre>

Then you can add the Emitter to your current scene like in my <a href="https://github.com/fritzvd/haxepunk-emitter-example/blob/master/src/MainScene.hx" title="MainScene.hx" target="_blank">MainScene.hx</a>
  
It looks like this:

<pre><code class="syntax actionscript">import com.haxepunk.Scene;
import Explosion;

class MainScene extends Scene
{
	private var explosion:Explosion;

	public override function begin()
	{
		explosion = new Explosion();
		add(explosion);
	}

	public override function update()
	{
        super.update();
        explosion.explode(230, 240);
	}
}
</code></pre>

Now run
  
`lime test neko`
  
And you should see something similar to the emitter above.

You can checkout my <a href="https://github.com/fritzvd/haxepunk-emitter-example" title="haxepunk-emitter-example" target="_blank">repo</a> and run it to play around with it.

I ran into this error below. It meant my sprite was too small. It took me a long time to realize that.
  
``