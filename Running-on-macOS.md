How to run the unsigned Deskflow app on macOS.

# Use `xattr` (and maybe `spctl`?)

> [!WARNING]
> `spctl` only works on macOS 14 and below, and won't work on macOS 15.
1. You _may_ need to do this, we're not sure:
```
sudo spctl --add --label "Approved" /Applications/Deskflow.app
sudo spctl --enable --label "Approved"
```

2. You will almost certainly need to do this:
```
xattr -dr com.apple.quarantine /Applications/Deskflow.app
```

3. You may also need to enable `deskflow` as well as `Deskflow`:
<img width="512" alt="macOS security settings" src="https://github.com/user-attachments/assets/7ab76129-8ddf-4a30-b308-560f9a423769">

4. If you don't see ` deskflow`, you may also need to:
    - Open the bundle: `open /Applications/Deskflow.app/Contents/MacOS/`
    - Drag all of the `deskflow*` binaries to the accessibility window.

# Use `anchore/quill` (unconfirmed)

[Quill](https://github.com/anchore/quill): Simple mac binary signing and notarization