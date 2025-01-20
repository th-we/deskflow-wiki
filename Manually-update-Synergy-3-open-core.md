# Synergy 3

Synergy 3 is proprietary software (for now) that uses the open source Synergy 1 Core (server and client). You can think of Synergy 3 as a pretty wrapper around Synergy 1 (which is open source software). Because of this, Synergy 1 Community Edition is compatible, which means you can patch Synergy 3 by building your own `synergy-core` binary.

# Compiler flags

By default, the `synergy-core` binary is only built by Synergy 3, but you can [build it yourself](https://github.com/symless/synergy/blob/master/BUILD.md) by running `cmake` with the `-DBUILD_UNIFIED=ON` arg.

The binaries are built into the `build/bin` directory.

# Apply the patch

> [!TIP]
> You may want to backup your existing `synergy-core` binary in case something is wrong with the one you built.

Once you have built your own `synergy-core` binary, simply copy it to the location where Synergy 3 is installed and overwrite the existing `synergy-core`.