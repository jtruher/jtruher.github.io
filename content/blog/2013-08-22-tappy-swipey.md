+++
title = "Tappy Swipey"
date = 2013-08-22T12:33:00-07:00
draft = false
slug = "2013/08/22/tappy-swipey"
+++

One of the early feature requests for Panic Attack, even before it was called that, revolved around user input.  People expected to slide, and were surprised and annoyed when their expectations weren't met.  I'm a people-pleaser, and I like trying to make things that people will enjoy using, so the next update will include a second, likely more-popular control scheme that closely mimics the one found in Planet Puzzle League, a Tetris Attack clone for the Nintendo DS.

It seems like a not-bad idea to describe why I built things the way I did.  I came at this project with a couple of strong biases: first, the original Tetris Attack for the SNES, and a freeware game called Crack Attack for desktop PCs.  Both had a kind of reticule thing - hitting a button would swap the two wrapped blocks.  My thinking, for my iOS version, was to just nuke the reticule and have the blocks swap if you tapped between them.  The context seemed obvious in my eyes, but - whoops! - hasn't been to others.

Now, one of the little details about my current scheme revolves around timing.  It's an important thing, for all of the versions I've played and enjoyed.  Things happen at a particular time, and take a bit of time for the animations to run through.  I lock blocks for a quarter of a second, giving the animation time to complete.  If you try to swap a locked block, you'll get a wiggle that says, hey, Cool It.  With this, the game seemed to play pretty well.

Enter the Swipe.  I've got it working now, actually, and. . .goddamnit.  It plays better than the tap.  I don't know if it's more intuitive, but it's definitely faster, because, at the moment, I've got a lot of the timing stuff sort of turned off.  You can press your finger down on a block to grab it, then tug the thing over, and everything just slides and is completely happy.  The quarter-second delay is broken.  The game seems to feel better for it, but now I'm worried that it'll completely break the feel of the game.  It'll certainly make tap-mode less appealing, since I don't think you can do as many things as quickly.

So - either I can force a delay into swipe mode and cripple it like taps, leave it as is and have a lame tap mode, or try to disable the delay for tap mode.  There's one little animation glitch with the current swipe mode, but it doesn't seem like a good enough reason not to turn something on for the sake of better gameplay.

Woof.  Compromises.
