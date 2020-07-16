+++
title = "Another Luxe Tip"
date = 2016-02-26T18:32:00-08:00
draft = false
slug = "2016/02/26/another-luxe-tip"
+++

I didn't expect to write more of these, but here I am!  I wanted to document a bit of interesting behavior I found in the process of building/rebuilding a shmup.

I had this cool effect for making a sprite kind of flicker and glow a bit by adding a duplicate and making it expand and contract rapidly.  I think the old way in SpriteKit used a parent/child relationship with an SKAction for the animation.  In luxe, the way I'm doing it is by attaching a component to the base sprite.

This component is fairly simple.  I build a sprite, attach it to its parent via the parent property (so moving it by hand is unnecessary), then add a few animations.  I've already learned that `onremoved()` is the right place to do teardown, so I destroy the sprite in there and all's well, right?  Not quite.

The extra wrinkle here is that I've got a timer that fires after a few seconds to remove the component.  Simple and straightforward - `entity.remove('flicker');` - until I tried to run it.  There's a couple of annoying subtle bugs in here that made me sad.

The first is the parent-child relationship built from the sprite.  The lifecycle of a sprite is this, during destroy.  First, destroy yourself, then loop through and destroy your children.  This means I'm double-destroying my flicker sprite!  Dangit.  The solution?  Don't add it as a child, and manually update position in `update()`.

The second is that timer.  See, there's a problem there, too: what happens if you kill the parent before the timer fires?  Everything gets cleaned up properly, but then you try to call `entity.remove('flicker')` and - boom, again!  Dangit.  The fix here was to save my scheduled timer and tell it to stop in `onremoved()`.  Both reasonably simple fixes, but real head-scratchers as I was working through the issues.  This isn't even a particularly complicated situation, but making simple mistakes really bit me in the ass.
