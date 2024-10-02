How to run the unsigned Deskflow app on macOS.

1. You _may_ need to do this, we're not sure:
> [!WARNING]
> `spctl` only works on macOS 14 and below, and won't work on macOS 15.
```
sudo spctl --add --label "Approved" /Applications/Deskflow.app
sudo spctl --enable --label "Approved"
```

2. You will almost certainly need to do this:
```
xattr -dr com.apple.quarantine /Applications/Deskflow.app
```

You may also need to enable `deskflow` as well as `Deskflow`:
<img width="512" alt="macOS security settings" src="https://github.com/user-attachments/assets/7ab76129-8ddf-4a30-b308-560f9a423769">
