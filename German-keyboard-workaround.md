# Problem

German Server -> Windows 10 -> German keyboard layout

German Client -> Manjaro Linux -> German keyboard layout

# Workaround

If the client swaps z and y, and can't write german letters correctly (öäüß) type "setxkbmap de" in terminal, now it works correctly.

If not working in i3 or KDE session with .xinitrc. Run this at x login:

```
cat setxkbmap.sh
#!/bin/bash
setxkbmap de
exit
```