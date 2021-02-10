---
layout: post
title: How to start Windows Twitch app minimized
categories: [twitch, autohotkey, ahk, script]
---

Simple AutoHotkey script:

```
Run, %APPDATA%\Twitch\Bin\Twitch.exe	;path to Twitch binary
FindAndClose:
if WinExist("ahk_class Chrome_WidgetWin_1") {
	WinClose
	Exit
}
Goto, FindAndClose
```

Save to text file, compile to exe with [Ahk2Exe compiler](https://www.autohotkey.com/download/ahk.zip) and put to autorun folder (type `%APPDATA%\Microsoft\Windows\Start Menu\Programs\Startup` into Explorer address bar). Don't forget to disable autostart in Twitch settings. Also you need to enable "When I Close the App: Hide Twich" option.
