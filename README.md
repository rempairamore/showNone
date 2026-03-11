# showNone
Quick macOS app to minimize all open windows (including Finder) with a Dock click. Made with AppleScript.

## How to Build It

Open Script Editor (in Applications > Utilities).
Paste this code:

```
on run
    -- Do nothing on initial launch
end run

on reopen
    tell application "System Events"
        set visibleApps to (every process whose background only is false and visible is true and name is not "Finder")
        repeat with anApp in visibleApps
            set visible of anApp to false
        end repeat
    end tell
    tell application "Finder"
        set collapsed of every window to true
    end tell
end reopen
```

Go to File > Save:

```
Format: Application
Name: showNone
Check "Stay open after run handler"
Uncheck "Show startup screen"
```

Drag showNone.app to your Dock.