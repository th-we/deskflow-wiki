# Running the unsigned Deskflow app on macOS

We do not yet sign our macOS app bundle, so you'll see the error:
> "Deskflow" is damaged and can't be opened.

![image](https://github.com/user-attachments/assets/22852f32-c4a9-4c1a-a362-ef8f1183833c)

## Solution

1. First, try [Apple's solution](https://support.apple.com/en-gb/guide/mac-help/mh40616/mac).

2. Failing that, try:
    - macOS 15 or higher: `xattr -d com.apple.quarantine /Applications/Deskflow.app`
    - macOS 14 or lower: `xattr -dr com.apple.quarantine /Applications/Deskflow.app`

3. You may also need to enable `deskflow` as well as `Deskflow`:
<img width="512" alt="macOS security settings" src="https://github.com/user-attachments/assets/7ab76129-8ddf-4a30-b308-560f9a423769">

4. If you don't see ` deskflow`, you may also need to:
    - Open the bundle: `open /Applications/Deskflow.app/Contents/MacOS/`
    - Drag all of the `deskflow*` binaries to the accessibility window.

## Other resources

Maybe of use to someone: [Quill](https://github.com/anchore/quill) is a simple mac binary signing and notarization.