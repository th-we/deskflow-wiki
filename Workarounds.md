## Contents
- [macOS: laggy cursor](#macOS-laggy-cursor)
- [macOS: Accessibility permissions](#macOS-accessibility-permissions)
- [macOS: Input Monitoring permissions](#macOS-input-monitoring-permissions)
- [macOS: Not working after upgrade](#macOS-Not-working-after-upgrade)
- [GNOME is missing tray icons](#GNOME-is-missing-tray-icons)
- [Input method mismatch](#Input-method-mismatch)
- [German keyboards](#German-keyboards)
- [AltGr key](#AltGr-key)
- [Remove Xdg Remote Desktop permission](#Remove-Xdg-Remote-Desktop-permission)


# macOS: Laggy cursor

## Problem
Using Wi-Fi on a MacOS client causes Deskflow cursor laggy.

## Workaround
Run this command in the Terminal

`sudo ifconfig awdl0 down`

Then type `ifconfig` to double check the status under the awdl0 section, it should be `status: inactive`.


# macOS: Accessibility permissions
(by [Trouffman](https://github.com/Trouffman))

For macOS, you need to allow the Deskflow process. 

1. Run: `xattr -c /Applications/Deskflow.app`
1. Go to: System Settings -> Privacy and Security -> Accessibility
2. Open Finder and go to Applications, right-click on 'Deskflow' -> Show Package Contents

![image](https://github.com/user-attachments/assets/7f0dce4d-ea18-480b-9420-540538a227be)

3. Go to: Contents -> MacOS
4. Drag & drop the file `Deskflow` into the Accessibility settings windows (opened in Step 1)
5. Enable both "Deskflow" and "Deskflow" 

![image](https://github.com/user-attachments/assets/081f156a-e702-457c-922e-1fddf3648a49)
* Unlike this image the newer version has Deskflow for both of these names one with the icon and the other a terminal application

# macOS: Input Monitoring permissions

For macOS, to send keystrokes to clients you need to give `input monitoring` access to the Deskflow process
 
1. Go to: System Settings -> Privacy and Security -> InputMonitoring
1. Click the + and find the Deskflow.app  (or drag and drop deskflow.app in the list) 

If you have upgraded deskflow you may need to remove the previous version and add the new one manually.

# macOS: Not working after upgrade

If you have manually installed you may need to reset the quarantine for the app: `xattr -c <pathof>/Deskflow.app`

Accessibility and Input Monitoring settings on macOS need to be removed and re-added sometimes when upgrading. If you are unable to remove the permission, make sure the application is not installed and restart the machine. Rebooting seems to remove no longer installed applications from the permissions. After you have removed the application the app should prompt when run and add itself correctly this time.


# Input method mismatch

## Problem

When you intentionally want to use different keyboard layouts on the client and server, you may experience a layout mismatch.

## Solution

Go to Preferences and uncheck the option: Use server's keyboard language on this computer (client mode)

# GNOME is missing tray icons
## Problem 

No Tray icons are visible under GNOME

## Solution 
Install the [Appindicator Support Extension](https://extensions.gnome.org/extension/615/appindicator-support/)


# German keyboards
## Problem

German Server -> Windows 10 -> German keyboard layout

German Client -> Manjaro Linux -> German keyboard layout

## Workaround

If the client swaps z and y, and can't write german letters correctly (öäüß) type "setxkbmap de" in terminal, now it works correctly.

If not working in i3 or KDE session with .xinitrc. Run this at x login:

```
cat setxkbmap.sh
#!/bin/bash
setxkbmap de
exit
```


# AltGr key

Support for AltGr is limited in Deskflow. Some users have good luck with remapping the Alt key to AltGr. You will have to use a config file for this, it is not supported in the GUI. Here are the instructions for that:

Start by exporting your current configuration, using File -> Save Configuration As.

Edit it using your favorite text editor, and find a section named Screens. Normally it looks like this:

 section: screens
   server:
      option1 = value
      option2 = value
      etc
   client:
      option1 = value
      option2 = value
      etc

What we want to do is add the option "alt=altgr" in the client section, like this:

 section: screens
   server:
      option1 = value
      option2 = value
      etc
   client:
      option1 = value
      option2 = value
      etc
      alt=altgr

Be sure to save this file someplace safe, where Deskflow will be able to find it but it won't be messed with, and point Deskflow to this file using the "Use existing configuration" option.

Some people have better results going the other way, using altgr=alt instead. Try this if you continue having troubles with the above example.

For recent versions of Deskflow, at least partial success has been reported with using

      altgr = shift

for the clients in the Screen section of the Deskflow configuration file (same place as above) instead.

## Modify altgr on linux

When running on linux you can set how the system defines altgr. 

You can use `setxkbmap -option [OPTION]` with one of the options below. Once you find a setting you like you can add it in to your user profile or run the command in a script running when you startup. 

 |  Option                  | Description |
 |:-----------------        |:------------|
 | lv3:switch               | Right Ctrl  |
 | lv3:menu_switch          | Menu        |
 | lv3:win_switch           | Any Win key |
 | lv3:lwin_switch          | Left Win    |
 | lv3:rwin_switch          | Right Win   |
 | lv3:alt_switch           | Any Alt key |
 | lv3:lalt_switch          | Left Alt    |
 | lv3:ralt_switch          | Right Alt   |
 | lv3:ralt_switch_multikey | Right Alt, Shift+Right Alt key is Compose |
 | lv3:enter_switch         | Enter on keypad |
 | lv3:caps_switch          | Caps Lock |
 | lv3:bksl_switch          | Backslash |
 | lv3:lsgt_switch          | Less/Greater |

Example autostart file 

This example comes from https://github.com/deskflow/deskflow/issues/4411#issuecomment-3210586777

Saved as `~/.config/autostart/keyboard-options.desktop`
```
[Desktop Entry]
Type=Application
Name=Keyboard Options
Exec=sh -c 'sleep 5 && setxkbmap -option lv3:rwin_switch'
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
```

> This adds a keyboard-options.desktop file with the content which ensures that the command is executed on startup. Can be viewed and adjusted in 'Startup Applications Preferences' as well.
The sleep can be adjusted there. I recommend keeping it, since if it's executed too early it can be overridden. I personally have it at 10 seconds and it works pretty well.


# Remove Xdg Remote Desktop permission
 
To remove the persistent token remove the `xdgRestoreToken` value from you Deskflow settings file. (~/.config/Deskflow/Deskflow.conf)
