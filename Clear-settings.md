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

1. Newer macOS:
```
defaults delete com.symless.Synergy.plist
defaults delete com.http-symless-com.Synergy.plist
defaults delete com.https-symless-com.Synergy.plist
```

2. All macOS versions:
```
rm -r ~/Library/Preferences/Symless
rm -r ~/Library/Synergy
rm ~/Library/Preferences/com.symless.Synergy.plist
rm ~/Library/Preferences/com.http-symless-com.Synergy.plist
rm ~/Library/Preferences/com.https-symless-com.Synergy.plist
```

Then run this command to clear the cached preferences stored in memory:

3. Newer macOS:
```
killall SystemUIServer
```

3. Older macOS:
```
$ killall -u $USER cfprefsd
```

# Linux

First, ensure that Synergy is uninstalled.

Run these commands to delete these files and folders (if they exist):
```
rm -rf ~/.config/Synergy/
rm -rf ~/.config/Symless/
rm -rf ~/.synergy/
```