+++
title = "Target-Action in Luxe"
date = 2016-03-09T16:55:00-08:00
draft = false
slug = "2016/03/01/target-action-in-luxe"
+++

There's an incredibly common, useful design paradigm called 'target-action', one I first encountered on iOS.  Basically, you've got a button that calls a function when something specific happens: maybe a touch or a drag or something.  This is the basis of all of iOS' user input.

So I thought it'd be handy to recreate something similar using the entity-component model.  It's pretty braindead-simple, but it seems to work okay for my purposes.  It's not quite as powerful as it could be, but given that I've already put together a game with it, I figure it's good enough.

Here's what the component looks like:

```
import luxe.Component;
import luxe.Input;

class TargetActionComponent extends Component {
  public var mouse_up_action : Void->Void;

  public function new(?_up_action : Void->Void) {
    super( {name: "targetAction"} );
    mouse_up_action = _up_action;
  }

  override function onmouseup(e:MouseEvent) {
    if(mouse_up_action != null && cast(entity, Sprite).point_inside(e.pos)) {
      mouse_up_action();
    }
  }
}
```

And here's what using it might look like:

```
var turkey = new Sprite({...});
turkey.add(new TargetActionComponent( function() { trace("I'm a turkey!"); } ));
```

The neat thing, and something I found pretty useful, is being able to rebind your target actions after creation.  That ends up looking something like this:

```
t.get('targetAction').mouse_up_action = function() { trace("Gobble gobble gobble!"); };
```

The obvious next step is adding more triggers and actions for various input events.  Touch events are a good thing to consider, as well as down-events, too - great for juicy, depressable buttons!
