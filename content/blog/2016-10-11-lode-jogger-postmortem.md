+++
title = "Lode Jogger Postmortem"
date = 2017-09-11T19:37:00-07:00
draft = false
slug = "2016/10/11/lode-jogger-postmortem"
+++


I (sorta) finished another [jam](http://itch.io/jam/gbjam-5), this time (mostly) making [Lode Jogger](http://jtruher.itch.io/lode-jogger)!

Hooboy.  This one was a doozy.

### What Is It?

Lode Jogger is a gameboy jam game designed to be a near-copy of Lode Runner, one of my favorite childhood games.  Players must run around a level, collecting treasure and avoiding the deadly monks, before escaping through the exit.

#### What Went Right

*Mechanics - Mostly*  

All of the bits of Lode Runner are here!  You can run around, you fall properly, you can climb ladders and go across ropes, and the crazy monks can do all of that, too!  Treasure works, digging works, everything's there.

It's a little bit clunky, sure, and I don't think I got ladders totally right, but I'll cut myself just a tiny sliver of slack.  About the only thing I was missing?  Monks can't pick up treasure!

*Pathfinding/AI*  

When it comes to jams, I usually try to avoid doing much of anything involving complicated AI.  Anything risky or too intensive generally gets tossed out as unfeasable.  With this, though, AI was kind of important.  The monks have to try to chase you, after all!

I distilled it down into basic pathfinding: monks will try to get you.  That means, of course, that I'm recalculating based on a grid.  It's pretty much just a slope field, with the bottom of the hill being wherever the player is.  They're smart enough to know that ropes might be the quickest way to get somewhere, though, which worked out nicely.  For anyone curious about the technical details, it's just a [dijkstra map](http://www.roguebasin.com/index.php?title=The_Incredible_Power_of_Dijkstra_Maps).

#### What Maybe Kinda Didn't Go Great

*Levels*

I had a fine test level for making sure all of the mechanics worked sensibly - you could collect treasure, you could die by falling into a pit, ladders and ropes seemed to work okay, and monks could follow you.

The bummer is that I more or less stopped at that point.  Whoopsie!  I definitely should have made more levels, but I think I was just under a lot of time pressure.

*Audio*

I basically completely punted on audio, full stop.  So.  At least it couldn't have gone worse, right?  I like the idea of basic bleeps and simple bfxr boops, but in practice most of the time they're complete earsores: too chirpy, scratchy, piercing.  I'll stick with no audio at all instead of garbage audio, and given how distracted I was by the other aspects, it's probably good that I didn't bother.

*Graphics*

I don't hate the gameboy palette, but I also didn't really put a whole lot of time or energy into the art of the game.  160x144 isn't a bad resolution to work in, but my artistic abilities were not really up to the task.  One of the rules of the jam was also that all assets must be made during the week: oops.  I punted on that big-time, too.

Having animated tiles for digging and dying would've been awesome, but again, time and lack of skill were both factors.  I think I was too anxious about getting some of the good parts done that I let a lot of stuff just kind of fall by the wayside.  Shucks!

#### Final Thoughts

I'm both proud and disappointed.  I poked at a few things that I haven't really worked on before, like basic pathfinding for the monks.

At the same time, Lode Runner is one of my top-tier favorite games, so not doing it justice stung a little.  It might be something I revisit later, but probably with a very different shell.  The GB palette's a little limiting, and I could do a lot better with a lot more of everything.  (Sound wouldn't be bad, either.  I loved the Mad Monk's Revenge soundtrack!)

