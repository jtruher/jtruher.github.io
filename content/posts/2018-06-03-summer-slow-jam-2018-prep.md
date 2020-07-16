+++
title = "Summer Slow Jam 2018 Prep"
date = 2018-06-03T10:02:00-07:00
draft = false
slug = "2018/06/03/summer-slow-jam-2018-prep"
+++

I’ve been doing the occasional game jam for awhile now.  They’re fun!  It’s nice to throw yourself at something for a short amount of time just to see if anything good comes of it - more often than not, it’s totally worth the minor time investment.  One thing that’s been a little annoying, though, comes down to infrastructure.

There’s a few different types of infrastructure, too, and maybe that’s a weird way to put it, but it’s the term I’m gonna use, so whatever!  The tools, code, art, assets you’ve built up over time all count as infrastructure, but what I mean here is a literal kind of infrastructure.

I’m going to back up just a little.  Eight years ago, Apple released Game Center, an iOS and MacOS service for high scores, matchmaking, online social stuff, the works.  It was exclusive to those two platforms and better than nothing, but had some warts and rough edges.  It also had a ton of green felt, which wasn’t great.

(As an aside, and particularly with Apple, be careful about using their technologies and frameworks if they’re not dogfooding it themselves.  How many games do they ship?  Zero?  Yikes.)

Back to infrastructure, though: Game Center was good enough for leaderboards, even if there were authentication challenges around valid high scores.  Trolling online scoreboards is a tough problem to solve at scale, but that’s not the point of this!

No, the point of this is that, for the Pigsquad Summer Slow Jams, I’m finally getting around to building my own online infrastructure.

Hold for applause.

It’s actually been kind of fun and interesting getting back into the online/server-y world.  I’m picking up Rails again for some dumb friggin’ reason.  It’s stuff I know sorta well, including all the warts, and the landscape has changed an awful lot since I stopped actively working with it ~7 years ago.  I mean, shit, Docker didn’t exist back then, mongrel was still the hottest shit (thanks, Zed Shaw!) and nobody was really grown up enough to know what they were doing.

It was total cowboy country, but it was kind of fun, in a way.

Thankfully, the scope is pretty limited here.  I figured, with the first technical theme being ‘minigames’, an arcade-y cabinet with a handful of Warioware-style games that can post scores to a web service would be pretty cool for seeing who does best.  And if I get this thing working and chugging well enough, who’s to say I wouldn’t ask other people to try banging on it, too?

Infrastructure is fun.
