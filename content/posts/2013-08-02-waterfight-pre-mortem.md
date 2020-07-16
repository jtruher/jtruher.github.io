+++
title = "Waterfight Pre-Mortem"
date = 2013-08-02T19:22:00-07:00
draft = false
slug = "2013/08/02/waterfight-pre-mortem"
+++

Like a lot of indies and hobbyists, I play around with a lot of prototypes.  Most of the time, these don't see the light of day, and for good reason - they're generally awful.  It's occurred to me more and more recently, though, that the cone of <s>shame</s>silence might be more appropriate for, say, Apple, and less appropriate for someone nobody's heard of.

So with that in mind, I thought it'd be a fun exercise to share some of my less-awful fiddlings, on the off-chance that someone finds them interesting.  If nothing else, these are great mistakes to learn from.  There's also the slim chance that they'll encourage me to actually finish them - finishing stuff's always a good thing, even if it's complete garbage.


### Initial Motivation
{% flickr_image 9423048349 n left "An early test with hue shifting." %}

There was a great article about [making caves with cellular automata](http://jeremykun.com/2012/07/29/the-cellular-automaton-method-for-cave-generation/) from. . .sheesh, back in March, I think.  [@madgarden](http://twitter.com/madgarden), one of my many nemeses, wrote a quick little C implementation and pushed a neat little toy game of life up onto the App Store.  When I saw this thing make caves, for some reason, my first thought was how they'd look if they were full of water, and you could drop ink into it to see it spread.  You'd have a fun little set of restrictions on where the water could go, and a bit of falloff as the ring lost momentum.

Crackpot idea, huh?  But it seemed like something that'd be neat to see working, so I promptly forgot about the idea for a month or two while I was trying to get Panic Attack shipped.  Eventually, I came back to it in the middle of May.  According to screenshots, it looks like I spent about a week playing around with it before interest fizzled.  It looks like this was, more or less, while Panic Attack was in review.  Go figure.

### What'd I Build?

{% flickr_image 9425814028 n right "Territorial spread in action.  I like the pretty teal." %}

What exists now is actually remarkably close to what the original idea was.  You can mark points on a 2d grid of colored cells, taking turns with your opponent in an attempt to control as much of the available space as possible.  Some of the mechanics don't work quite as you'd expect, but this is. . .techno. . .something, not water.

### What Went Right, and Why?
The cellular automata stuff got hooked up and working really, stupidly fast.  I pretty much have @madgarden to thank for that.  I also tried doing something a little different.  For nerd talk, the game is pretty much just a big grid of CALayers.  I overlap them slightly, such that their borders rest on top of their neighbors.  I offset the colors just slightly on each, fiddling with small deltas on saturation and luminance, and I think it turned out really kind of pretty.

Doing colors with HSB rather than RGB is something I'm probably going to do more and more going forward, particularly in places where I want to keep a fairly distinctive color scheme but want to keep some kind of interesting noise.  This was a trick I first tried playing with on the dumb LD26 project - that'll get one of these pre-mortems, too, at some point.

### What Sucked, and Why?
The game itself was kind of slow.  This is because I'm doing things in a thickheaded way.  It's definitely not shippable as it stands now, but maybe moving to some of the new iOS7 stuff will make it tolerable.

The UI/interaction stuff is also godawful.  It was getting better near the end, but it was really hard to tell what the hell was going on, and what various taps would do.  It was barely usable for me, and certainly doesn't pass the Spouse Test.

### What's Next?
Maybe iOS7, but probably nothing.  It looked pretty, at least, so it has that going for it.  I'm not even sure there's much of a market for this, so at best it'd probably just be a free app.
