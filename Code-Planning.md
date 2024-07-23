# Summary

This page details long-term plans for the code base.

1. We will implement Wayland support with [libei](https://gitlab.freedesktop.org/libinput/libei)
1. The GUI source code will be migrated gradually from `/src/gui/src/` to `/src/lib/gui` and `/src/cmd/synergy`
1. The daemon (`synergyd`) will be rewritten in Rust and will be cross-platform:
    - It will simply a watchdog for the client/server.
    - IPC will be done over Unix sockets instead of TCP (Windows now has `AF_UNIX`).
