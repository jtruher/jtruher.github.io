+++
title = "Luxe status bar"
date = 2016-03-25T10:14:00-07:00
draft = false
slug = "2016/03/25/luxe-status-bar"
+++

Another in a long series of brief tips!  If you'd like to hide the status bar on iOS (unconfirmed, so far, for Android), just set fullscreen to true in `project.flow`.  If you want this just for mobile devices, it's likely easiest to do in `config`

```
override function config(config:luxe.AppConfig) {
  #if mobile
    config.window.fullscreen = true;
  #end
}
```

Boom!  No more status bar!
