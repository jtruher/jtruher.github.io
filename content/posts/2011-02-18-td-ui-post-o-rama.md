+++
title = "TD UI Post-O-Rama"
date = 2011-02-18T23:04:00-08:00
draft = true
slug = "2011/02/18/td-ui-post-o-rama"
+++

There was an interesting discussion the other day between [@madgarden][1], [@ChronoSoft][2], and [@Podesta1971][3] about user interfaces in iOS games.  Well, unfortunately I was a little under 
the weather, and unable to give a decent response in a tweet or two.  Naturally, 
this means I'm going to word-vomit a bit, instead.  But at least we'll get 
pictures, too!  Hopefully this'll push me to do more postmortem posts.  They 
seem like they'd be fun to write, so we'll see. 

![][4]

So, to start, here's a very early screen, with just a level being loaded.  It has the proper placement and size of tiles, but little else.  Lots of decisions to make!

![][5]

Like, say, what to do around the edge of the screen.  A border seemed natural, 
as the original had one, and hey, why shouldn't mine?  This was just some simple 
photoshop filter munging, but helped to draw things together.  Also in place 
are new tiles, some of which stuck around until the very end.  Some of the 
other tiles are placeholders, though the knight also survived to the end.  Go, 
RLTiles, go!





![][6]



Adding more, now, this time with a shaded-in bottom half and a real minimap. 
 Note the pluses - those are due to drawing a square path, rather than a square 
shape.  Important distinction, one which surprised me for a little while.





![][7]



Getting a lot closer now, and ready to actually discuss some of the UI ideas. 
 My first inclination was to have some kind of sliding panel system at the 
bottom of the screen, which is what those dots were meant to help distinguish. 
 Each panel would be a different color as well, helping you to figure out what 
kind of thing you were looking at. 





![][8]



Like, say, armor.  You could tap on an item to activate it, and it'd highlight 
(in the case of equipment) or vanish (in the case of consumables).  Unfortunately, 
the sliding panels meant that people didn't really know that there was anything 
to do with that lower panel, which led to confusion and frustration.





![][9]



The sad part is how far I ended up getting with everything before having to 
tear all of this stuff down.  I had some neat looking gradients, and pretty 
decent-ish presentation, given how little art-time was involved.  This didn't 
exactly look bad, to me, and even now it isn't terrible, but thinking about 
it today, it definitely feels like a local maximum.  This is an example of 
the best that a simple developer can do without any outside art design or influence. 
 Be afraid!





![][10]



And this is what happens when you start using whatever you have available. 
 The [lostgarden.com][11] stuff, by Daniel Cook, is super awesome and 
super free.  Find whatever art you can, slice it, dice it, and throw it in. 
 It's amazing how much better things look with simple borders, curved corners 
and a bit of darker, transparent gray.  Note the buttons just plastered on 
there, and how much better the paperdoll model looks than the previous, sliding 
panel/box tappy system.  Getting much better.





![][12]





And, to round this off, I'll finish here, with something more or less the finished 
version.  Up until now, it's basically been show and tell, which is fun, but 
not terrifically helpful for anyone trying to glean anything useful.  So, with 
that in mind, here's a list of my general thoughts and guesses.





1. Make buttons look like buttons.  People need to know that something means 
'click me'.  Maybe it's got a gold border, or blinks/pulsates.  Buttons should 
feel *good* to press, even if it's a fake, screen button.



2. Rounded corners are cheap ways of making things look better.  It's turd-polishing 
territory, but hey.  Along those same lines, adding just little touches here 
and there can really make a surprising difference.  Darken/drop shadows, or 
make the backgrounds of touchable things darker than their surroundings, or 
even just making a font slightly larger can accumulate to make a world of difference. 
 Go look at some of the Trainyard progression for proof or inspiration - Matt 
Rix did a phenomenal job.



3. Iterate, iterate, iterate.  Don't let stupid live, or it'll fester, and 
you'll never be rid of it, because you'll think it's necessary.  It is very 
easy to trick yourself into thinking that something with a lot of time sunk 
into it needs to stick around.  Treat those as learning experiences, cull, 
and move on.  (Besides, if you're wrong, that's what version control is for, 
right?)



4. Keep your gameplay separate from your UI.  Start with a real game, or you'll 
be screwed.  You'll also know if your UI is good if it keeps your game as fun 
as it always was.  If you find yourself annoyed or frustrated by stupid crap 
after adding some 'great' new feature, hey, maybe re-evaluate that feature. 
 For instance, I've been pissed at my own UI for awhile - it's cumbersome and 
sucky to use potions/equip new gear, and generally difficult to tell what's 
better than what you've got.













[1]: http://twitter.com/madgarden (@madgarden)
[2]: http://www.twitter.com/ChronoSoft (@ChronoSoft)
[3]: http://www.twitter.com/Podesta1971 (@Podesta1971)
[4]: https://lh4.googleusercontent.com/_5O1JDvh1Go4/S25vjQ_AQGI/AAAAAAAAMDU/8uMK_xFey7c/s800/Screen%20shot%202010-02-06%20at%204.27.57%20PM.jpg
[5]: https://lh3.googleusercontent.com/_5O1JDvh1Go4/S3UaJ0iej9I/AAAAAAAAKgM/J7d9pzKwsYg/s800/Screenshot_3.jpg
[6]: https://lh3.googleusercontent.com/_5O1JDvh1Go4/S3ZfNVmbbgI/AAAAAAAAKkE/2qN6BSb1w5s/s800/Screenshot_14.jpg
[7]: https://lh3.googleusercontent.com/_5O1JDvh1Go4/S7Jyd8xdhzI/AAAAAAAALM0/ezAYIR-SOGY/s800/Screenshot_64.jpg
[8]: https://lh5.googleusercontent.com/_5O1JDvh1Go4/S7PMDDmFOFI/AAAAAAAALKY/63mzWmwwEIg/s800/Screenshot_76.jpg
[9]: https://lh5.googleusercontent.com/_5O1JDvh1Go4/S-XHgM-zGeI/AAAAAAAALmc/S41w93A2VYs/s800/Screenshot_111.jpg
[10]: https://lh4.googleusercontent.com/_5O1JDvh1Go4/S_g9JjLFR7I/AAAAAAAALqY/zqzEWMjdYqM/s800/Screenshot_142.jpg
[11]: http://lostgarden.com
[12]: https://lh6.googleusercontent.com/_5O1JDvh1Go4/TBQCv6VKX2I/AAAAAAAAL0Y/oabhhaZ5_t4/s800/Screenshot_175.jpg