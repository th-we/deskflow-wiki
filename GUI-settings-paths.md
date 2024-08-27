# GUI Settings Paths

**v1.15.0 or higher**

- *Windows:* `\HKEY_CURRENT_USER\Software\Synergy\Synergy`
- *macOS:* `~/Library/Preferences/com.symless.Synergy.plist`
- *Linux:* `~/.config/Synergy/Synergy.conf`

**v1.14.x or lower**

- *Windows:* `\HKEY_CURRENT_USER\Software\Synergy\Synergy`
- *macOS:* `~/Library/Preferences/http-symless-com.Synergy.plist`
- *Linux:* `~/.config/Synergy/Synergy.conf`

# Clear GUI Settings

## Soft-reset

If you have v1.15.0 or higher, use the GUI to reset the settings.

![image](https://github.com/user-attachments/assets/4b62b8c7-b585-432f-bbf3-1999a91c17f1)

## Hard-reset

For a more thorough reset, you can delete the actual files on disk.

**Windows:**

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

**macOS:**

First, ensure that Synergy is uninstalled.

On newer macOS versions, you'll need to use `defaults delete` to clear the settings cache:
```
defaults delete com.symless.Synergy.plist
defaults delete com.http-symless-com.Synergy.plist
defaults delete com.https-symless-com.Synergy.plist
```

For all macOS versions, delete any files on disk:
```
rm -r ~/Library/Preferences/Symless
rm -r ~/Library/Synergy
rm ~/Library/Preferences/com.symless.Synergy.plist
rm ~/Library/Preferences/com.http-symless-com.Synergy.plist
rm ~/Library/Preferences/com.https-symless-com.Synergy.plist
```

On older macOS versions, you'll need to kill the `cfprefsd` process to clear the cache:
```
killall -u $USER cfprefsd
```

**Linux:**

First, ensure that Synergy is uninstalled.

Run these commands to delete these files and folders (if they exist):
```
rm -rf ~/.config/Synergy/
rm -rf ~/.config/Symless/
rm -rf ~/.synergy/
```