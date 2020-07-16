+++
title = "How I Make App Icons"
date = 2014-04-24T18:43:00-07:00
draft = false
slug = "2014/04/21/how-i-make-app-icons"
+++

Art is a pain in the butt.  I flinch whenever I have to do anything substantial any kind of image editor - Pixelmator, Photoshop, or whatever.  It's always been kind of a goal to minimize the number and size of assets in my app bundle.  In general, smaller apps are good for everyone.

For The Dungeon, one of the few outright app rejections was because my app icon didn't match my big-icon.  This kind of surprised and annoyed me at the time, but now I feel like Apple was probably doing me a favor.  For Panic Attack, I wanted to try something different with my icons, and render them in code rather than doing anything in an art program.

Which brings me to today!  I've been working on a pixel editor for ~~far, far too long~~ a little while, and finally got around to putting together an icon for it.  I'm doing it all in code with pretty simple, straightforward Core Graphics calls.  It might not be all that optimal, but it lets me specify sizes and point/pixel scaling at whim, which makes editing and regenerating all my icons at all required sizes remarkably painless.

<!--more-->

Let's start small.  We're just going to start with a few things of importance, to me.  We're going to turn off antialiasing to get nice, crisp lines and turn off interpolation to make sure things that have to be scaled up end up looking nice as well.  The general pattern is as follows: make a graphics context, do some drawing, then pull it out and close your context.

``` objectivec
    UIGraphicsBeginImageContextWithOptions(size, YES, scale);
    CGContextRef ctx = UIGraphicsGetCurrentContext();
    CGContextSetAllowsAntialiasing(ctx, false);
    CGContextSetInterpolationQuality(ctx, kCGInterpolationNone);

    /* Drawing goes here! */

    UIImage* finalImage = UIGraphicsGetImageFromCurrentImageContext();
    UIGraphicsEndImageContext();
```

{{< image src="/img/icon-step-1.png" position="left" style="border-radius: 8px; float:left; margin: 10px;" >}}
<!-- {-% img left /images/icon-step-1.png %} -->
Okay!  So we've got something now.  Neat!  Let's draw something other than plain black.  I happen to have this cheerful little robot guy, so let's draw him.  Remember - drawing code goes with that little comment up above.  Black is pretty boring, so let's add a happy little robot!

``` objectivec
    UIImage* robot = [UIImage imageNamed:@"radrobot.png"];
    [robot drawInRect:robotRect];
```

{{< image src="/img/icon-step-3.png" position="left" style="border-radius: 8px; float:left; margin: 10px;" >}}
<!-- {-% img right /images/icon-step-3.png %} -->
Black is pretty boring, though.  Let's do a really simple background of squares.  One of the [things](/blog/2013/08/02/waterfight-pre-mortem/) that turned out kind of neat back with an earlier prototype was using HSB for neat little grids of faintly-different squares, so let's use a similar technique to get a rad background going.

What are we actually about to do?  Well, we decide that we want a certain number of chunks, then we loop over our size by certain amounts.  We pick a color, plunk down a rectangle in our graphics context, then repeat until the whole thing is filled.  There's a subtle bug here, but that'll be left as an exercise to the reader.  One 'nice' thing about this is, because our output is good, we don't much care about whether the code is 'correct'.  (I promise: it probably isn't, but it's more than good enough to keep moving forward.)

``` objectivec
    int chunks = size.width / 2;

    for(int x = 0; x < size.width; x += size.width / chunks) {
        for(int y = 0; y < size.height; y += size.height / chunks) {
            [[UIColor colorWithHue:208.0 / 360.0 saturation:0.25 brightness:arc4random_uniform(32) / 32.0 * 0.125 + 0.725 alpha:1.0] set];
            CGRect target = CGRectMake(x * size.width / chunks, y * size.height / chunks, size.width / chunks * 2, size.height / chunks * 2);
            CGContextFillRect(ctx, target);
        }
    }
```

{{< image src="/img/icon-step-4.png" position="left" style="border-radius: 8px; float:left; margin: 10px;" >}}
<!-- {-% img left /images/icon-step-4.png %} -->
This is actually looking pretty good, but it's a bit flat and uninteresting.  A simple radial gradient might be just the ticket - or a linear one, even.  I'll leave that as an exercise for the reader.  Unfortunately, this is one of the more complicated, less-obvious bits of this whole mess.  I mean, we've got straight-up RGB values thrown into some array, color spaces, and yuck.  This might be one of the right places to have drawn a simple radial gradient in Pixelmator, `drawInRect:` the image and called it a day.

{%img right /images/icon-step-2.png %}
This is just a shot of the squares, for sake of comparison.  The individual colors and squares don't much matter, because the goal is really just a sense of depth.  It's pretty easy to tweak the `arc4random_uniform(32)` and multipliers to adjust your color ranges.  I reference [this picker](http://hslpicker.com) a ton to make sure I have some sense of what I'm going to get on the other side.  Sometimes, though, I just tweak, test and rebuild until I get something appealing.

``` objectivec
    CGGradientRef myGradient;
    size_t num_locations = 2;
    CGFloat locations[2] = { 0.0, 1.0 };
    CGFloat components[8] = { 1.0, 1, 1, 0.5,  // Start color
        0, 0, 0, 0.5 }; // End color

    CGColorSpaceRef baseSpace = CGColorSpaceCreateDeviceRGB();
    myGradient = CGGradientCreateWithColorComponents (baseSpace, components,
                                                      locations, num_locations);

    CGPoint myStartPoint = CGPointMake(size.width / 2, size.height / 2), myEndPoint = CGPointMake(size.width / 2, size.height / 2);
    CGFloat myStartRadius = 0.1, myEndRadius = size.width;
    CGContextDrawRadialGradient (ctx, myGradient, myStartPoint,
                                 myStartRadius, myEndPoint, myEndRadius,
                                 kCGGradientDrawsBeforeStartLocation);

```

{{< image src="/img/icon-step-5.png" position="left" style="border-radius: 8px; float:left; margin: 10px;" >}}
<!-- {-% img left /images/icon-step-5.png %} -->
Wow!  That's a lot less flat, and probably something similar to what I'm actually going to use for the shipping app.  This method has a number of advantages if you're photoshoppically challenged - but if you've got an actual graphic designer, this might not be especially practical for you.  At the end of the day, do what you can to make something you're happy with.  That's pretty much the real lesson here.
