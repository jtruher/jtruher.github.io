+++
title = "1-Bit Clicker Jam: Clickenville"
date = 2017-04-14T10:00:00-07:00
draft = false
slug = "2017/04/14/1-bit-clicker-jam-clickenville"
+++


I've been wanting to do another jam for awhile.  I like the two week cycle, but haven't seen any themes or jams that really struck my fancy.  The technical limitations ones went well in the past, so those are the ones I tend to go after.

This time, it was a 1-bit (black and white graphics) clicker (mouse only) jam.  Perfect!  My idea was to go after something that was a little bit like Spaceplan or a cookie clicker-esque game.

#### What Is It

Clickenville is a game where you try to throw money at your problems.  You have a number of buildings that provide income and offer upgrade options.  These buildings let you alter the world of the game how you see fit, improving things for the residents, the town, and the world as a whole.

#### What Went Right

This was my first experience writing a more substantial shader.  The theme being a 1-bit clicker made me think, with my limited art skills, that doing a cool dithering shader would be the best way to go.  That way, I could find a tileset that looked good under this visual transformation and save myself a lot of effort in the process.

It'd also kind of hearken back to some of the games I played as a kid back on a black and white computer.  Atkinson dithering was pretty great back then, and doing something that resembled it sounded like a fun project.

Plus, Obra Dinn looks great with a (much better) dithering technique.

This was also a chance to poke a little bit at a different way of building up content.  I knew going into it that having a whole lot of different kinds of buildings with interconnected systems and resources would be a pretty neat feature.  Say, you could have a guild that trained adventurers, then send them off to explore a dungeon.  Some of these adventurers might die along the way, which would leave bones for necromancers to use.

I didn't really start out whole-hog on doing something data-driven at first, because I didn't really understand what I wanted.  Once I got a few basic classes and a really simple workflow going, though, I started pulling everything out and ended up with a little ruby script that reads a bunch of json and writes out a bunch of haxe classes for my in-game content.  It worked pretty well, even if augmenting this system over time was a bit of a challenge.

#### What Didn't Go Great

It's funny, I always start writing my postmortems in this section.  This time around, I basically pretended that audio didn't exist.  There's neither catchy music nor bleeps, and certainly no bloops.  It's always something I neglect and something I'm not tremendously proficient with, so it's kind of a self-fulfilling prophecy.  Someday I'll aim more for doing better audio work, but this time I was focused way more on the neat shader and the general mechanics.

A few mechanics are still missing, unfortunately.  I wanted a workflow where you'd start off with really basic buildings and had to spend resources to unlock them, but it kind of fell out along the way.  I didn't have a great handle on how the UI ought to look or work, and letting people know what something cost was a bit of a challenge - both for unlocking buildings and for letting people know what a particular upgrade would cost.

#### Final Thoughts

Is it done?  Heck no.  Am I happy with it?  Mostly, sorta, yeah.

Game jams are always a [question of time](https://www.youtube.com/watch?v=9pt7EWFF_T8) but more buildings would be top of my list.  Doing a full UI pass to make things make more sense would also be pretty important.

The big takeaway that I had was: well, I had everything interactable hardcoded.  Was this necessary?  Why couldn't you plunk down a Blacksmith wherever the hell you wanted, if you had the funds?

This meant, in a broad way, that I was putting together an RTS instead of a simple clicker.  Oops.  Neat thought, though.
