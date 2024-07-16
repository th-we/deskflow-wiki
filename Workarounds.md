# macOS laggy cursor

## Problem
Using Wi-Fi on a MacOS client causes Synergy cursor laggy.

## Workaround
Run this command in the Terminal

`sudo ifconfig awdl0 down`

Then type `ifconfig` to double check the status under the awdl0 section, it should be `status: inactive`.

# German keyboards
'# Problem

German Server -> Windows 10 -> German keyboard layout

German Client -> Manjaro Linux -> German keyboard layout

'# Workaround

If the client swaps z and y, and can't write german letters correctly (öäüß) type "setxkbmap de" in terminal, now it works correctly.

If not working in i3 or KDE session with .xinitrc. Run this at x login:

```
cat setxkbmap.sh
#!/bin/bash
setxkbmap de
exit
```

# AltGr key

Support for AltGr is limited in Synergy. Some users have good luck with remapping the Alt key to AltGr. You will have to use a config file for this, it is not supported in the GUI. Here are the instructions for that:

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

Be sure to save this file someplace safe, where Synergy will be able to find it but it won't be messed with, and point Synergy to this file using the "Use existing configuration" option.

Some people have better results going the other way, using altgr=alt instead. Try this if you continue having troubles with the above example.

For recent versions of Synergy, at least partial success has been reported with using

      altgr = shift

for the clients in the Screen section of the Synergy configuration file (same place as above) instead.