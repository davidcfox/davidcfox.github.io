---
layout: post
title: "Add Sublime Text to Windows Context Menu"
description: "Adding Sublime Text to the Windows Context Menu via a .bat command"
category: "Windows Tips"
tags: ["windows", "sublime", "useful tip"]
---
{% include JB/setup %}

I finally gave into peer pressure and installed Sublime Text on my computer.  I have to say that I am enjoying it far more than my beloved Notepad++.  One of my frustrations was that there was not a context menu open to open files with Sublime.  A quick Google search brought me to this [Gist](https://gist.github.com/mrchief/5628677/) that easily added the context menu I was after.

<!--more-->

If you don't want to follow the link above, here are the instructions:

First, Create a .bat file with the following code in it:

    @echo off
    SET st2Path=C:\Program Files\Sublime Text 2\sublime_text.exe
    rem add it for all file types
    @reg add "HKEY_CLASSES_ROOT\*\shell\Open with Sublime Text 2" /t REG_SZ /v "" /d "Open with Sublime Text 2"   /f
    @reg add "HKEY_CLASSES_ROOT\*\shell\Open with Sublime Text 2" /t REG_EXPAND_SZ /v "Icon" /d "%st2Path%,0" /f
    @reg add "HKEY_CLASSES_ROOT\*\shell\Open with Sublime Text 2\command" /t REG_SZ /v "" /d "%st2Path% \"%%1\"" /f
    
    rem add it for folders
    @reg add "HKEY_CLASSES_ROOT\Folder\shell\Open with Sublime Text 2" /t REG_SZ /v "" /d "Open with Sublime Text 2"   /f
    @reg add "HKEY_CLASSES_ROOT\Folder\shell\Open with Sublime Text 2" /t REG_EXPAND_SZ /v "Icon" /d "%st2Path%,0" /f
    @reg add "HKEY_CLASSES_ROOT\Folder\shell\Open with Sublime Text 2\command" /t REG_SZ /v "" /d "%st2Path% \"%%1\"" /f
    pause

Next, run a command prompt with Administrator privileges and execute the .bat file you created.

It really is that easy.
