> [!WARNING]
> WIP: This is a bit rambly and needs more structure.

Here's our general philosophy about CI vs dev env.

We believe it's a mistake to try to match CI on local dev env because the more you try to replicate CI locally, the more you compromise your setup configuration; it becomes more complex and buggy. This is why we don't maintain build scripts; each build script is like a mini-program with its own bugs.

It's wrong to impose our local dev env settings on other people. In a way, this is almost as bad as forcing everyone on the team to use the same IDE.

CI is there to force consistency in the codebase.

Why we don't want to maintain a `CMakePresets.json` file: A CMake presets file seems like a good thing at first, but it actually promotes laziness.