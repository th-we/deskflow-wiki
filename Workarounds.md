## Contents
- [macOS: laggy cursor](#macOS-laggy-cursor)
- [macOS: accessibility access](#macOS-accessibility-permissions)
- [macOS: Not working after upgrade](#macOS-Not-working-after-upgrade)
- [Input method mismatch](#Input-method-mismatch)
- [German keyboards](#German-keyboards)
- [AltGr key](#AltGr-key)


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
4. Drag & drop the file `deskflow` into the Accessiblity settings windows (opened in Step 1)
5. Enable both "Deskflow" and "deskflow"

![image](https://github.com/user-attachments/assets/081f156a-e702-457c-922e-1fddf3648a49)


# macOS: Not working after upgrade

If you have manually installed you may need to reset the quarantine for the app: `xattr -c <pathof>/Deskflow.app`

Accessibility settings on macOS need to be removed and re-added sometimes when upgrading. If you are unable to remove the permission, make sure the application is not installed and restart the machine. Rebooting seems to remove no longer installed applications from the permissions. After you have removed the application the app should prompt when run and add itself correctly this time.


# Input method mismatch

## Problem

When you intentionally want to use different keyboard layouts on the client and server, you may experience a layout mismatch.

## Solution

Go to Preferences and uncheck the option: Use server's keyboard language on this computer (client mode)


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