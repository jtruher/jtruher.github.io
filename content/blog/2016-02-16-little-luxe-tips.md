+++
title = "Little Luxe Tips"
date = 2016-02-16T11:02:00-08:00
draft = false
slug = "2016/02/16/little-luxe-tips"
+++

I'm not dead!  A shock, I know, but between real-life obligations and a decline in my general state of gives-a-crap, my fun little hobby life has suffered in recent months.  Shucks.

Doesn't mean I can't bounce back, though, right?  Spring 2015-ish, I was on the hunt for something new to tinker with, and I found [this rad stuff](http://snowkit.org).

First off, a dumb, semi-obvious one.  For anyone loading textures in `config`, using something like `config.preload.textures.push({ id:'assets/playershot.png' });` who want nearest neighbor filtering on all of their textures, it's important to call `phoenix.Texture.default_filter = phoenix.Texture.FilterType.nearest;` *before* you load anything.  Promise - this'll make you sad and confused otherwise.  Obvious in hindsight and a real forehead-slapper once I figured it out.

Another important thing to note is that someday (soon?) phoenix is going to go away, replaced with [embers](http://snowkit.org/2015/09/14/snowkit-dev-log-7-embers/).  The API might look similar, and this might still be relevant, but just something to keep in mind.

I bumped into another forehead-slapper obvious issue with global events and ids.  It's super easy to just `Luxe.events.listen('whatever', function() { doRadStuff(); })` - but the gotcha here was not holding onto what `listen()` returns.  Whoopsie.  That's the thing you use later to unlisten to things, ala `Luxe.events.unlisten(event_id)`.  The worst part?  This is even [in the docs](http://luxeengine.com/docs/guide.events.html)!  Bad me.

The last tip is going to be a bit of a rambler.  Luxe supports the pretty useful entity-component model of design: you've got your base entity, and you can lump additional behavior onto it via components, which are small little focused nuggets of goodness.  I'm coming from an objc/iOS background, which means that I spotted new, init and destroy and thought, aha!  That's clearly the place to put stuff!

D'oh.  Nope.  See, the thing you're attaching your component to isn't quite ready in new - that's just for building stuff up.  Init, too, is a little early - sure, you'll be ready, but if you want to add stuff your component after the fact (adding components to an entity returns that built component - handy for twiddling stuff immediately afterwards) - well, onadded is a better place.  Teardown is similar, as onremoved happens earlier in the destruction lifecycle than ondestroy.
