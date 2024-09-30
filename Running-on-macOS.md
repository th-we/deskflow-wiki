To run the Deskflow app on macOS, you may need to run these commands:
```
sudo spctl --add --label "Approved" /Applications/Deskflow.app
sudo spctl --enable --label "Approved"
xattr -dr com.apple.quarantine /Applications/Deskflow.app
```

You may also need to enable `deskflow` as well as `Deskflow`:
<img width="512" alt="macOS security settings" src="https://github.com/user-attachments/assets/7ab76129-8ddf-4a30-b308-560f9a423769">
