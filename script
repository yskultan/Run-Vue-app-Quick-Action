tell application "Finder"
	--set path from selected folder as value
	set thePath to the selection
end tell
--convert path to posix syntax
set thePath to quoted form of POSIX path of (thePath as alias)

tell application "iTerm"
	--check if iTerm is already running
	set createdWindow to false
	--if it's not running create window
	if it is running then
		if (count windows) is 0 then
			create window with default profile
			set createdWindow to true
		end if
	end if
	--if running create tab
	if not createdWindow then
		tell current window
			create tab with default profile
			tell current tab
				launch session
				tell the last session
					--chnage directory to folder's path, install dependencies and run app
					write text "cd " & thePath & " && npm install" & " && npm run serve"
				end tell
			end tell
		end tell
	end if
	activate
end tell
