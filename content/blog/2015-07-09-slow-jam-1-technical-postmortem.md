+++
title = "Slow Jam 1: Technical Postmortem"
date = 2015-07-09T10:59:00-07:00
draft = false
slug = "2015/07/09/slow-jam-1-technical-postmortem"
+++

Yesterday, I posted up some of my recent thoughts and experiences on the last PIGSquad game jam.  It went pretty well, and I'm pretty happy with it!  This is going to be the big, ugly breakdown of how I actually put the whole thing together.

And just to repeat myself, here's the [page for the game](http://jtruher.itch.io/3720-1)!

<!--more-->

I've mentioned this before, but I've been doing a lot of work and research with luxe, a game engine built on top of Haxe.  It's all pretty new and different for me, coming primarily from a recent iOS background - but that's for another post.

Luxe is in alpha, which means it isn't quite finished yet.  Luxe, more importantly, is completely badass.  Damn and blast, I was going to talk about this another time.

I'm not going to cover what I brought up yesterday - we all know it's a spaceship game.  Instead, I'll go into how I actually put this whole thing together, from start to finish, with a bit of a focus on Luxe.  Like with C, Luxe starts you off in Main.  It's the entry point for the whole app (as far as I understand - apologies in advance, __discovery).  For me, it's also where I keep a few important, app-wide things, like where we're at in a state machine, and the starfield background.

#### Background Starfield

Speaking of which, that background is something that turned out really well.  I'm pretty proud of how I put it together, so let's start there.  In Pixelmator, I added noise, tweaked light and dark balance and fiddled with it until I got black with a sea of stars.  From there, I duplicated that layer and ripped out anything black, leaving just stars.  That layer, with just stars and no black background, was duplicated a couple more times.  The trick here is that I went in with the eraser and just swept through it, leaving patches of stars here and there.

Now, the engine part of things.  Each of those transparent layers gets to live as a texture on its own quad.  Simple uv coordinate manipulation - adding a delta on each frame - makes the texture slide across the quad (or Sprite, if you prefer the luxe term).  Each quad also gets its own delta speed, adding basic parallax.  Finally, I provided a basic setter to Main, the class containing this whole thing, so that any state could change the speed that the game went at.  Simple, straightforward, and pretty clean.

#### Physics

One of the physics simulations luxe supports is called Nape.  Nape is pretty darned good, and more than sufficient for my purposes.  Putting it to good use is left as an exercise for the reader, but my general scheme was to put together a couple of simple static boxes: one would keep the player ships from exiting the view, and the other served to clean up any bullets or asteroids that bumped into it.  It was a pretty straightforward system.

Nape, in particular, is pretty cool because of the rich callbacks system.  I can define certain physics bodies as one type, and others as another, then get a function called when the two bodies interact.  It's how all of my collision works: when two asteroids bump, I spawn a little explosion.  When a bullet hits an asteroid, same thing.  When an asteroid hits a player, explode a lot!  Oh, and kill that poor helpless ship, too.

#### Input

Input was pretty straightforward, too.  Luxe comes with an entity component system right out of the box, so I put this to good use.  My InputComponent ended up being a bit of a God Object, which isn't great - but, hey, game jam.  It's okay if things are a bit clunky or poorly designed, as long as it works.  Input holds onto the particular ship's physics body and attaches to the ship's Sprite.  Each frame, I update the sprite's position and rotation based on its physics body.  (This is how asteroids and bullets work, too.)

One trick that I apply here, I think picked up from [@madgarden](http://www.madgarden.net) is to give the acceleration a boost when the player tries to move in the opposite direction of travel.  So, if you're heading right and going fast, then try to go left, give a bit more oomph to the physics impulse until your velocity normalizes.  It makes everything a lot zippier and feels pretty great, once you've tuned whatever that extra-oomph is.

#### Data-Driven Nonsense

I think this came up in yesterday's overall post, but going into the last day, I put together a basic json-based data file for ship stats.  This was after I'd already gotten the whole game up and running.  This was huge, because it meant I could see where the hardcoded numbers are, and set them up accordingly in the json.  My InputComponent, after it's been loaded, can ask Main about what ship it's made and assign values out of the data file.

It was almost offensive how well this system worked, and it's something I plan on re-using for other projects.  The only failing: the lack of testing.  If I had my druthers, I'd put together something that let me twiddle and toggle game settings on the fly, rather than having a lengthy rebuild/relaunch cycle.  Being able to disable ship death and tweak ship settings in-game would have been huge.  Maybe for the next jam!  (But probably not, knowing me.)

#### Music

This is probably going to earn its own post at some point, but figuring out how to do loops and samples in Garage Band was pretty great.  I stepped through a bunch of their supplied loops, dragged in the ones that sounded good, then set them to loop over a particular interval until I got something I liked.  The one trick that I found handy was to separate an intro from a main game loop.  This seemed like a good way of doing things, because in luxe there's a completion handler for when a sound effect will end.

That's most of the interesting chunks.  Doing this project in luxe has really gotten me excited again about building stuff, and I'm looking forward to the next gamejam in August (July's has a schedule conflict for me, sadly).  I'm also looking forward to just having an easier, cross-platformier dev environment.  After being iOS only for so long, being able to blast something out to a bunch of different places feels pretty great.
