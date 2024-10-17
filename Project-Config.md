> [!WARNING]
> **WIP:** This mostly encapsulates our ideas, but needs more work.

> [!NOTE]
> **TODO:** Add tips and tricks to help devs adapt to this philosophy.

> "The more you try to force things, the more you're gimping your project." -- Chris (@sithlord48)

Here's our general philosophy about CI vs dev env.

# Don't match CI

We believe it's a mistake to try to match CI on local dev env because the more you try to replicate CI locally, the more you compromise your setup configuration; it becomes more complex and buggy. 

It's wrong to impose our local dev env settings on other people. In a way, this is almost as bad as forcing everyone on the team to use the same IDE. CI is there to force consistency in the codebase later down the line in the developer's workflow. Trying to pre-empt this causes frustration for devs.

# No scripts

Why we don't maintain build scripts: Each build script is like a mini-program with its own bugs. Scripts look like the right choice because they're easy to write, but actually, very little of the time taken is spent on writing them initially and you'll spend an eternity maintaining them.

# No presets

Why we don't want to maintain a `CMakePresets.json` file: A CMake presets file seems like a good thing at first, but it actually promotes laziness. Qt Creator, for example, makes it look like you have you have to select a preset (even though it is optional) and so developers are likely to do this rather than figuring out what settings they should set.