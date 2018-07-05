How to remove all Synergy settings and config files for a clean uninstall/reinstall.

# Windows

First, ensure that Synergy is uninstalled.

Run `regedit` and delete these registry keys (if they exist):

* `HKEY_CURRENT_USER\Software\Symless`
* `HKEY_CURRENT_USER\Software\Synergy`

Now, delete these directories (if they exist):

* `%ProgramData%\Symless`
* `%ProgramData%\Synergy`
* `%ProgramData%\Synergy v2`
* `%USERPROFILE%\AppData\Local\Synergy`
* `%USERPROFILE%\AppData\Local\Symless`

# macOS

First, ensure that Synergy is uninstalled.

Run these commands to delete these files and folders (if they exist):
 
`$ rm -rf ~/Library/Preferences/Symless`
`$ rm -rf ~/Library/Synergy`
`$ rm ~/Library/Preferences/com.https-symless-com.Synergy.plist`

Then run this command to clear the cached preferences stored in memory:

`$ killall -u $USER cfprefsd`

# Linux

First, ensure that Synergy is uninstalled.

Run these commands to delete these files and folders (if they exist):

`$ rm -rf ~/.config/Symless/`
`$ rm -rf ~/.synergy/`