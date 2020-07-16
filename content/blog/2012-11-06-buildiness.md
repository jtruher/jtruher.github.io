+++
title = "Buildiness"
date = 2012-11-06T20:40:00-08:00
draft = false
slug = "2012/11/06/buildiness"
+++


For quite some time now, I've had a bit of a wild hare about something incredibly stupid.  After being pestered a few too many times about getting a TestFlight build while away from my computer, I thought, hey, it'd be sweet if I could, from my phone, tell the damned machine to make a new build and push it up to TestFlight.

So, one weekend when I was particularly full of beans, I gave it a quick, vicious stab.

<!--more-->

Thankfully, someone else already solved a hell of a lot of this problem.  My minor contribution is a bit of AppleScript-y magic that fires a script off from an iMessage (which, in light of their reliability, was maybe not my best choice.  Still, it hasn't missed a build so far.)

What's the practical use of this? For one thing, if I can keep project sizes small (let's say under half a meg) it ends up being faster for me to push everything up via this script, then use TestFlight to install on all of the various devices I'm building for.  All of the things I'm working on are Universal and support iOS 5.1, so I've got: a 3GS, a 4, an iPad 1, and a now-horrifically-embarrassingly out of date iPad 3 (which I adore.  Seriously.  It's what I've been doing all of my blogging on).

The other, somewhat less silly part about this is that I don't *actually* need a computer for development.  Well, sure, I need something to go compile some shit, but I don't actually need it with me.  I was inspired by some lunatic's story about ditching his laptop for an iPad/linode server, and this is kind of like the poor man's version of that.  No slight intended to Textastic (which is great) but it doesn't make Obj-C development as easy as Xcode.  Shucks.

It's sure as hell good enough to muddle about, though, and learning not to depend on newfangled tools is probably a good thing for anyone to learn. It's also not the worst debugging feedback loop I've ever worked with, though by golly, does it come close.

First, I started off using the following [GitHub gist](https://gist.github.com/2411095).  It's really what's doing most of the heavy lifting.  It'll clean your builds, make the project, sign with a provisioning profile, then curl it on up to TestFlight.

``` bash
#!/bin/sh

# Current as working as of 2012/4/17
# Xcode 4.3.2

PROJECT_ROOT="$HOME/SomeDirWhereYourProjectLives/XXXXXXXX"

WORKSPACE="$PROJECT_ROOT/XXXXXXXX.xcodeproj/project.xcworkspace"
CONFIG="AdHoc"
SCHEME="XXXXXXXX"
SDK="iphoneos"
TARGET="XXXXXXXX"
BUILDDIR="$HOME/build$TARGET"
OUTPUTDIR="$BUILDDIR/AdHoc-iphoneos"
APPNAME="XXXXXXXX"
DEVELOPER_NAME="John Doe (PRTG45V3X)"
PROVISIONING_PROFILE="$PROJECT_ROOT/XXXXXXXX.mobileprovision"

echo $BUILDDIR

cd $PROJECT_ROOT

echo "********************"
echo "*     Cleaning     *"
echo "********************"
xcodebuild -alltargets clean

# echo "********************"
# echo "*     Archiving     *"
# echo "********************"
# xcodebuild -workspace $WORKSPACE -scheme $SCHEME archive

echo "********************"
echo "*     Building     *" 
echo "********************"
xcodebuild -sdk "$SDK" -target $TARGET -configuration "$CONFIG" OBJROOT=$BUILDDIR SYMROOT=$BUILDDIR

echo "********************"
echo "*     Signing      *"
echo "********************"
xcrun -log -sdk iphoneos PackageApplication -v "$OUTPUTDIR/$APPNAME.app" -o "$OUTPUTDIR/$APPNAME.ipa" -sign "$DEVELOPER_NAME" -embed "$PROVISIONING_PROFILE"

API_TOKEN="ZZZZZZZZZZZZZZ"
TEAM_TOKEN="YYYYYYYYYYYYYY"
RELEASE_NOTES="TBD"

# remove the old zipped dSYM
rm -rf "$OUTPUTDIR/$APPNAME.app.dSYM.zip"
# zip up the new dSYM, we must cd to where the dSYM is or the zip command will zip up tons of intermediate dirs
cd $OUTPUTDIR
zip -r -9 "$OUTPUTDIR/$APPNAME.app.dSYM.zip" "$APPNAME.app.dSYM"

curl http://testflightapp.com/api/builds.json \
  -F file="@$OUTPUTDIR/$APPNAME.ipa" \
  -F dsym="@$OUTPUTDIR/$APPNAME.app.dSYM.zip" \
  -F api_token="$API_TOKEN" \
  -F team_token="$TEAM_TOKEN" \
  -F notes="$RELEASE_NOTES" -v

echo "********************"
echo "*    Cleaning up   *"
echo "********************"
echo $BUILDDIR
rm -Rf "$BUILDDIR"
```

Also, you might need to do this just before signing, in order to unlock the keychain:

	security unlock-keychain -p YOUR_PASSWORD "$HOME/Library/Keychains/login.keychain"

The trick, for me, is that I keep all of my projects in my Dropbox folder.  I'd prefer not to have my build directories live in there, where they'll be muddling with files a bunch, so I have my DerivedData actually spit out into ~/build instead.  (I somehow got this to work through Xcode, too, though I now have no friggin' clue how.)

I've also got this AppleScript hooked up to fire in Messages on message received events.  It checks against who sent the message in order to only fire the script if I've asked it to do work.  It'd be kind of cool to have a smarter whitelist, but for now, this is good enough.  I've tried making it a bit smarter to clear out the unread badge count, but my script-fu is not quite strong enough.  Consider it an exercise for the reader!

    using terms from application "Messages"
    	
    	on message received theMessage from theBuddy for theChat
    		-- display dialog (theBuddy's name as string)
    		set whoDidIt to full name of theBuddy
    		-- display alert whoDidIt & who & theMessage & huh
    		if whoDidIt is equal to "Jim Truher" then
    			tell application "Terminal"
    				activate
    				do script "automatedBuildAndUploadToTestflight.sh " & theMessage & ";exit"
    			end tell
    		end if
    		
    	end message received
    	
    end using terms from
    
After using this system for a few weeks, it's occurred to me that the really neat, useful part about this whole workflow is that I can end up pushing TestFlight builds a hell of a lot more easily now than I could before.  It's really pretty fantastic.
