---
layout: post
title: TextMate - Large print edition
categories: 
- mac os
- textmate
- tech
description: guide to fixing TextMate's odder text size settings
keywords: TextMate,mac os,blogging,howto,guide,text size,font size,eyestrain
---


Maybe I'm getting old. Maybe my eye test in 2 days' time will prove expensive. Maybe I'm just tired.

Whatever the cause, TextMate's text size is just too small for me this evening. Turning up the text size of the document being edited is easy: Preferences > Fonts & Colors, fiddle with the last setting in the pane, job done. Changing the drawer (the file list on the left), that's a bit trickier...

### Find the .app file

Mine's in my Applications folder

### Get the source files

Right-click on the app name, and choose Show Package Contents

Navigate to Contents > Resources > English.lproj

Open Project.nib (double-click is fine)

### Happy hacking

Locate the FileHierarchy window (may need to find the Project.nib window and double-click on FileHierarchy)

Click where it says "Text Cell", navigate to Font > Show Fonts and adjust to taste

Save your changes and restart TextMate

### The really tricky bit (part the first)

What you have probably just done is rendered the text in the lefthand pane illegible thanks to text clipping and overlapping. It's what I did. Let's fix that.

Open the Size Inspector

Click underneath and to the right of where it says "Text Cell". The whole panel should be selected.

Change the Row Height (about 5 units larger than the font size you've just picked seems to be a good starting point)

Save. Restart TextMate

### The really tricky bit (part the second)

Better? Good. One more thing

Click directly underneath "Text Cell". Just the lefthand part of the panel should be selected.

Change the width (make wider)

Save. Restart TextMate (repeat last 2 steps to taste)

### Want to shortcut the process?

Well, you don't get to customise it as much but, you can always just [copy mine](http://github.com/lizconlan/textmate-settings/tree/master/English.lproj/ "my new settings on github") if you like. Back up your old settings first!