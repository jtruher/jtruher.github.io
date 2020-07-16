+++
title = "What's a Game?"
date = 2015-04-28T22:44:00-07:00
draft = false
slug = "2015/04/28/whats-a-game"
+++

Some people like to carefully proofread what they write and post on the Great Wide Internet™.  It's a good philosophy!  It leads to quality content (for your braaaand) and, in general, it's how things ought to be done.

This is not gonna be one of those things.  Strap yourselves in, folks, I'm going completely free association, here.

Backing up a step, I've been playing around with [luxe](http://www.luxeengine.com) for the last few weeks, hence the silence.  Ludum Dare went Very Poorly, but unfortunately I don't know the Latin for that.  'Vilissimo', sayeth the googles.  The sad part is that it's all stupid emotional nonsense, but that's not what I'm here to fumble with.

I've been building a silly little couch party game for the last few nights - since Friday, come to think of it.  Or maybe last Thursday (4/23/2015).  The first night, I got a whole level loaded from [Tiled](http://www.mapeditor.org)!  I've never done that before, so it was kinda neat to see such quick turnaround.  Slowly but surely, I'm learning.  Second and third night, all physics, then input.  Now I've got these neat little marbles that roll around the screen, more or less how I imagined my prototype, way back when.  Triggers are hooked up, so I know when things bounce into bad things, and...

Wait.  Shoot.  I'm forgetting something.  The whole, uh, game part of gamedev.  This is just fiddling and playing around - valuable, for sure, and certainly when trying to pick up something new and slippery, but I can't really play this.  Games generally have goals, some have scores.  Even games with emergent fun, whatever the hell that is, tends to have some kind of structure in place.  So far, this is just a toy.  Which loops back to why I'm here!

What's a game, in the kind of base, boiled-down sense?  Is it just a set of rules, simple or complex?  Pong's a game, right?  At its core, Pong is a game that ends when someone's lives hit zero.  Aha!  That means, in my game, I need to keep track of each player, decrement some counter when a particular event happens, and call the game 'over' when there's only one person left standing.  Right?

Well, sure.  But what if it was a little different?  What if there was a flag, and each marble had to steal/knock it away from the other marbles to take it back to their little cubby?  How do you structure that?  I guess that's where I'm at.  Luxe (bless it) has this pretty common, rad, new-to-me Entity-Component system.  I've got a Sprite, and I attach Input to it, and bam, it moves.  I attach Physics, and shazam, it affects its world, while the world around it affects it.  (I've combined the two for convenience, but you get the point).

Which, after a whole lot of hot air and sore fingers on my part, leads to the conclusion: are Game Modes for this Dumb Marble Game just components that I can bolt onto...what?  Having them attached to the sprites themselves seems a little too low-level, truth be told.  What if the game object, the thing that holds the world, and the sprites, and receives the callbacks for collision, is the one I lump this thing onto?

Well, now we're getting somewhere, aren't we?
