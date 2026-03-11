# showNone

A simple macOS utility to minimize all open windows — including Finder — with a single click on its Dock icon.

Built with AppleScript.

---

## How to Build It

1. Open **Script Editor** (found in `Applications > Utilities`).

2. Paste the following code:

```applescript
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

3. Go to File > Save:

- Format: Application
- Name: showNone
- Check "Stay open after run handler"
- Uncheck "Show startup screen"

4. Drag showNone.app to your Dock.


## Custom Icon

1. Download the PNG image from this repo (or create your own one).

2. Right-click showNone.app > Get Info.

3. Drag the PNG onto the icon in the top-left corner of the Get Info window.

4. Close the window—the icon updates automatically.