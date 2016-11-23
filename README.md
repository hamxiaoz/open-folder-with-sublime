# open-folder-with-sublime
A Finder toolbar icon to open current selected file/folder with Sublime.

![](/demo.gif)

## How to use?
- Download [the zip file](https://github.com/hamxiaoz/open-folder-with-sublime/raw/master/Open%20With%20Sublime.app.zip)
- Unzip to Applications folder (or any folder that you won't mistakenly delete the app)
- Right-click to open to pass the Mac security check
- Hold `Option+CMD` and drag the application to toolbar
- Enjoy

## How to create the app manually?
Open AppleScript Editor, copy the following source and export as Application.

```
(*
 Open in Sublime Text
 To use:
  * Drag Open In Sublime Text to the toolbar of any finder
  window to add it to the toolbar
*)

on run
	tell application "Finder"
		if selection is {} then
			set finderSelection to folder of the front window as string
		else
			set finderSelection to selection as alias list
		end if
	end tell
	
	subl(finderSelection)
end run

-- script was drag-and-dropped onto
on open (theList)
	subl(theList)
end open

-- open in Sublime Text
on subl(listOfAliases)
	tell application "Sublime Text"
		activate
		open listOfAliases
	end tell
end subl
```

## Credits:
- Source: [Brian Schlining's Blog](http://hohonuuli.blogspot.com/2013/07/open-filesfolder-selected-in-finder.html)
- Icon: https://github.com/jamiewilson/predawn/tree/master/dock-icons
