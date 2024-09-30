To run the Deskflow app on macOS, you may need to run these commands:
```
sudo spctl --add --label "Approved" /Applications/Deskflow.app
sudo spctl --enable --label "Approved"
xattr -dr com.apple.quarantine /Applications/Deskflow.app
```
