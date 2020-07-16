+++
title = "Summer Slow Jam 1 Postmortem"
date = 2015-07-08T18:42:00-07:00
draft = false
slug = "2015/07/08/summer-slow-jam-1-postmortem"
+++

It's been awhile!  I missed each and every one of you.  At least I haven't been sitting on my thumbs during my long-ish silence.  Promise!

Before we get too far, here's the [page for the game](http://jtruher.itch.io/3720-1)!

<!--more-->

So, PIGSquad, a local group of gamedev enthusiasts, is pretty great.  Recently, they started this neat Summer Slow Jams thingie - each month this summer is a different jam with a different theme (or set of themes).  I like game jams, but most of the 48/72 hour ones are a bit too rushed for me.  Family obligations make it difficult to really focus, too.  A week, on the other hand. . .

A week is a pretty healthy amount of time.  The general theme was "something you can showcase" and the game-specific themes were: seed, spirits, in the fast lane, explosions(!), brewfest, guilty pleasures, wild west, and man vs machine.  Most of these didn't really say much to me, and the overall prompt of a showcase-worthy game was a bigger barrier than the game themes, honestly.

(One interesting thing about the themes - at least two of them are total gimmes.  Guilty Pleasures and Explosions pretty much let you build whatever the hell you want - what game couldn't use more explosions?  It was a neat trick to make it easier for everyone to contribute and come up with something.)

First off, before you can really start on anything, you have to, uh, think about what the hell you're doing, right?  For jams, I usually just sit and stare at the theme for awhile and waited for stuff to fall out.  Seed, spirits, brewfest, and guilty pleasures didn't yield much immediately.  I had a neat hook for man vs machine that was basically a cyborg metroidvania with some of the corruption mechanics from Breath of Fire: Dragon Quarter - you had rad robo-abilities, but using them made you more inhuman.  I stopped myself at 'metroidvania' and filed that away for later.

Which left only a few more options.  I had a hook for wild west: basically, a timing/reaction game with two players, where one had to move an analog stick in a certain way to draw a pistol, aim, and fire, but it felt too fiddly and didn't strike me as particulary "showcaseable".  Yes, that's a word, as of now.

In The Fast Lane was the first thing I ended up building a prototype for.  I had the idea of doing a Grandma Simulator, where you're an old lady sitting in the fast lane, oblivious to the traffic crashing behind you.  It seemed a little cruel and mean, and again, not all that showcaseable.  (My standards on what's worth showcasing might, upon reflection, be a little bit high.)  I kept thinking about it and ended up doing a kind of Road Rage simulator, instead.  I wired up simple boxes with basic movement to fake up what actual freeway traffic was like.  It worked, but it didn't strike me as particularly zazzy, so I shelved it.

Time from first code written to discard: maybe a day or so?  On a 48h jam, I probably would've just had to stick out the crappy prototype, but I knew I had a bit more time to let things noodle and build.  Probably a good thing, too, given how fiddly the cars felt.  Tuning physics for game feel is tricky, and adding decent AI drivers felt like a big challenge.

It was Tuesday before I settled on a different idea, going with something else I thought of on the first night of the jam, using the theme of Explosions instead.  I had pretty decent shmup sprites, and a fairly good grasp of what makes those fun to play, so I settled on a cooperative Asteroid Field Navigation game, with a dash of Star Wars in-joke to boot.  3720 : 1 (3720 to 1) was born-ish!

It didn't hurt that I'd, more or less, done this already before.  A shmup that I've been writing since the Kennedy Administration had a neat asteroid field mechanic, where occasionally these white ping-pong balls of death and sadness would rain down on you and the aliens.  Dodging them was fun and shooting them was fun - why not make a whole game around that one mechanic?  It seemed like it'd work.  Scaling back weapon effectiveness and making it a team effort could help keep the game interesting and challenging.

Which meant that I had to get to work, and work I did!  Though, looking back, not nearly as much as I should have.  The fun umbrella of personal issues kept me from being as productive as I ought to have been, leading to some last-minute issues.  Things got done, but not up to my usually high standards.  This being a jam is no reason for clumsiness or cludginess.

My choice of tools were probably the thing that really saved me.  I used Pixatronic to generate my spaceship sprites and the asteroids, Pixelmator for the rad parallax starfield (probably my favorite part of the whole shebang), bfxr for sound effects, Garage Band for the music and, last but absolutely not least, luxe for the engine.

Garage Band is a little cheesy, but the track for that turned out pretty well, too.  Figuring out how to put together simple loops was fun, and completely worth the half-hour invested.  This is a tool I'll absolutely use again the next time around.  Moving forward, I'd like to add a few more loops to alternate between, rather than just an intro and a single loop.  Variation is good, and making different loops is as simple as toggling channels on and off.

Luxe let me put together everything with remarkable speed and not a whole heck of a lot of code.  How much code, you ask?  This much!

```
-------------------------------------------------------------------------------
Language                     files          blank        comment           code
-------------------------------------------------------------------------------
haXe                             7            242             74           1003
JSON                             1              0              0             98
-------------------------------------------------------------------------------
SUM:                             8            242             74           1101
-------------------------------------------------------------------------------
```

Note that little chunk of JSON!  Another thing I'm pretty happy with is having a set of ships, loaded from a file!  It's odd where the low bars and the high bars are, huh?  It's something I wanted to do on bullet heck for ages, and just couldn't handle, or couldn't get around to it.  C'est la vie.

Before I get too much further, remember the theme I'd chosen: Explosions!  I had, uh, one.  It wasn't a bad one - a simple circle that appears and shrinks, with a bunch of squarish particles flying everywhere.  Probably not the worst explosion in the world, but it could have done with a lot more polish and tweaking.  This is an area I'd definitely like to give more attention going forward, particularly when it comes to ships exploding.  They should knock asteroids around when they go kaboom!  At least I've got screen shake.

Going into the big jam demo night, I had a main menu screen, a ship selector screen (for up to 4 players) and a game screen.  Each worked - mostly.  The ship selector had a few bugs, and there were a few little issues with the game, too.  I'm proud that I was able to get them fixed mid-jam-demo, but less proud that I let them slip at all.  One of the things I've been reluctant to do, with jams, is commit to working in a team.  I've always been concerned that I won't be able to work fast enough, or won't be able to contribute enough.

Next time, however, my plan is to take on a team of friends and have them be extra sets of eyeballs.  This experience is some proof that I can push something decent enough out without completely driving myself mad.  Everything I caught in the last few hours could've been spotted earlier - with another set of eyes, or more people.  Given the next jam topic is going to be multiplayer games, all the more reason to get more people involved.  The fact that I've already written a multiplayer game for a jam (partially unintentionally) only helps my case.

What's more, on the final demo night, I'll be able to have other people around to talk and show off the work.  I absolutely suck at self-promotion and talking about my work, so this is going to be a huge boon to me.  I dreaded showing it to people, and really hope the next time around goes even better than this time.

The mechanics of scoring could have used a bit of help and explanation.  Basically, you earn points (parsecs) based on how far forward the furthest ship is.  The gameplay idea was to have someone in a quick ship towards the more dangerous part of the asteroid field, where fast reflexes were most necessary, and have the other players hang back and try to shoot asteroids out of their path.  There isn't much of a visual explanation of this effect - probably something added to the score bar would help in that regard.

Knowing which ships to pick is also a bit of a challenge.  The star explanations for ship capabilities are. . .well, that was one of the last things I did, on the day of the jam.  I was throwing numbers into JSON and hoping nothing broke.  More work on ship balance is going to be necessary to call this actually finished and done.

At the end of the day, I'm pretty darn happy with how this project turned out - happy enough to actually post it for people to fiddle with.  I learned a lot about working with luxe, making music, not leaving things until the last minute (cough, cough) and just putting together a general framework for more of these types of games.  The general blocks and chunks are going to be really straightforward to pull out for the next multiplayer work.

If you'd like to try it, head to my [itch page](http://jtruher.itch.io) to give 3720:1 a try.  It's still a little clumsy in a lot of ways, but I'm still happy with how it turned out.  Feedback is always welcome, and the best place to hit me is probably my [twitter](http://twitter.com/jtruher).
