# Sequoia firewall and security problems

macOS 15 Sequoia introduced new firewall and security features which [caused problems](https://9to5mac.com/2024/09/19/security-bite-macos-sequoias-filewall-is-disrupting-security-tools-and-more/) with some apps. The quickly released 15.0.1 patch helped a little, but did not solve the problems completely.

**Fixed:** The macOS 15 Sequoia firewall and security problems have now been fixed by Apple in the 15.1 minor update (not to be confused with 15.0.1 patch). Please update to 15.1 to solve the firewall and security problems.

# Running the unsigned Deskflow app on macOS

We do not yet sign our macOS app bundle, so you'll see the error:
> "Deskflow" is damaged and can't be opened.

<img width="274" alt="image" src="https://github.com/user-attachments/assets/23e1d6ee-e922-47cf-a6ea-0a515f366057">

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