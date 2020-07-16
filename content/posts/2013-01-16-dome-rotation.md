+++
title = "Dome Rotation"
date = 2013-01-16T22:45:00-08:00
draft = false
slug = "2013/01/16/dome-rotation"
+++

I've been playing around a bit with a few little iOS apps, and one of the annoying things I've come across is how rotation is handled: specifically, how it isn't quite handled by your views.  It is, from a certain point of view, just fine, but from another, it's completely nuts.

Every UIView has what's called a transform - the linear algebra explanation is that it's a 3x3 matrix that mucks about with your UIView's box in 3d-space.  This is all well and good, until you ask for your view's center after rotating.

Read that again.  Okay.

So, time for a quick test.  Portrait mode, iPad, what's my center?  {384, 512}.  Width, height, all well and good.

Rotate to landscape (so now we're wider than we are tall).  What's the view's center?  {384, 512}?  Uh.  Hm.

Were you expecting that?  I sure as heck wasn't.  I don't really have a great solution for this yet, either, so if you're like me, and enjoy positioning crap based on your view's coordinates, you might be a little sad.  Fear not, however!  There's a semi-awful solution that isn't too hardcore stupid.  In your view controller, just add a few methods:

``` objectivec
-(CGPoint)center
{
	return CGPointApplyAffineTransform(self.view.center, self.view.transform);
}

-(CGRect)frame
{
	return CGRectApplyAffineTransform(self.view.frame, self.view.transform);
}

```

As always, test and log thoroughly before taking this at face value.  Also, this means that instead of doing self.view.center, you'd end up with just self.center.  Both'll work fine in portrait, but only one'll be happy with all rotations.