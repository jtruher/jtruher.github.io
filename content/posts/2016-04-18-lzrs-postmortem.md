+++
title = "LZRS Postmortem"
date = 2016-04-18T12:16:00-07:00
draft = false
slug = "2016/04/18/lzrs-postmortem"
+++


I've been pretty sloppy in the past about recapping when I've actually managed to finish something.  This is an attempt to be a bit more proactive and a bit less "oh right, I should've done that weeks ago" about a project.  This time around: [LZRS](https://jtruher.itch.io/lzrs) for #lowrezjam2016!

#### What Is It

LZRS started out due to an interest in the laser section from Mega Man 2.  Yes, this whole game is basically just poking and prodding at a single mechanic.  Lasers flying across the screen that the player needs to avoid to navigate an environment felt like a decent hook - I mean, clearly, given that a MM game used it!

Because I'm lazy, I tend to throw procedural generation at just about anything I come up with, so in this case, my initial idea from long ago was to make a generator for screens, or levels, or courses, or whatever.  This makes total sense, because content takes time to make, but it also creates another problem: now you've got to make the thing that *actually* makes the thing, which can be more work.  "Fun" is tricky to algorithmically generate.

And that, sadly, is where the idea sat until a few weeks ago.

#### What Went Right

* It finished!

Bear with me, here - for someone chronically late on side projects, actually getting something semi-satisfactory done is a big deal (to me).  Having two weeks instead of two days contributed heavily, as did having a general idea before I even knew about the jam.  Most of the time, I try to start from the theme, but here the theme is more about a technical limitation, rather than creative.  That's an interesting distinction to me.

* Platformer

It's a platformer!  Usually people tend to start with these, but not me!  I'm not really very good at real-time, actiony games, likely due to lack of experience.  It's pretty exciting to have something finished that plays reasonably well.  Collision happens, there's triggers, stuff goes fwhoosh, and it all seems to behave as I'd expect.  (Whether things behave as players expect is another matter entirely.)

* Reception

People seem to like it!  I haven't woken up to any severed heads in my bed, which I consider a good sign.  It's short enough that most people should be able to finish it, and nobody's complained about getting bored, either.


#### What Maybe Kinda Didn't Go Great

Usually you go with five specifics, but to heck with that.  I do what I like

I think most of what I'm unhappy with boils down to one word: incomplete.  It's a jam game, and I was pushing back and forth against what seemed like a good idea to add, and what seemed possible within the remaining time.  A few hours a night is an awful lot if you're driven with a plan, but for exploration, it ends up being a bit trickier.  Experimentation is fine but it really helps if you think your new idea is going to bear fruit.

(And before I go too much farther, incomplete is from my perspective as the dude who saw everything it could have been, rather than the players going through the whole thing.  Very different perspectives.)

First off, the big mechanic: lasers.  Sure, they slide around, or turn themselves on and off, but from a mechanical perspective, they're kind of lame, aren't they?  There's no telegraphing, there aren't any hints about whether they're going to turn off soon, or even which kind of laser is which!  It's a little lame.  They don't move at different speeds, and they're not even textured.  Tons of work could be done here polishing and improving.

Audio's one big area that I'm a little disappointed with, and would probably get tackled pretty soon.  Just looking at the main spaceman character is a great start: sounds for footsteps, jumps, hard landings, skids - there's plenty here that I could add to push a bit more depth and feel into things.  Heck, just having multiple different sounds for the same type of event would be great for adding feel and juiciness.

This next one's a bit tricky to explain, but the unfinished-specific umbrella is probably just 'polish'.  I've usually got a pretty discerning, ruthless eye about what works, what doesn't, and what to change.  Some of the tiles don't work quite right, but more importantly, my tiles are all black with alpha.  Why care?  Well, I can't really tint them, which makes me kind of bummed out.  I like being able to just tweak colors a bit, and if they're white instead of black, I can muddle with the levels as much as I'd like.

The backgrounds change as you progress through the level, after all, so why not the walls and the environment, too?  This was another issue of "things work, so don't break anything" that kept me from making too many daring changes.  The hard deadline both helped and hurt me, bless its heart.  Twiddling with the precise color progression for the background would likely be on my list, too, just to make sure it's exactly what I want.

I've been thrilled by people posting their times and death counts and would love to have some kind of global leaderboard for scores.  I don't know that I want to do anything platform-specific, which means either picking something cross-platform or finding an acceptable third-party solution.  I haven't really gotten that far or done any thinking about it yet, but it'd be a great thing to have.

Lastly on this hate train: levels and courses.  Courses feels like the right word for the sequence of, uh, ten or eleven laser-filled screens of death.  I didn't even consider it for the scope of the jam because, well, there's no way to pick a different course on the menu.  Duh!  Having a bunch of courses with different themes or different mechanics would be really pretty great.  Designing the levels wasn't quite as rough as I was afraid it'd be, and making more of them might be fun.

#### Final Thoughts ~Brainfarts~

I'm tremendously happy with how things turned out.  I've been itching to do Ludum Dare for ages, but the 48/72 deadlines are a bit too much for someone with a dearth of time.  Having two weeks and a technical restriction made all the difference in the world, and I think going in with an easily-applicable concept helped a ton.

The game even seems pretty fun, which is always a pleasant surprise.  The mechanic isn't mine, but I can claim some of the level design, at the very least.  It was a good experience and something I wouldn't at all mind putting more time into.  That alone probably makes this experiment a success.
