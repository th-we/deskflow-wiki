## Short Term Goals:
We want to finish these in the near future

1. Code Modernization and Cleanup, A lot of our code base is very old and needs updating, unused code paths should be removed and use of older methods should be updated. Our code base requires C++20 we should be using as many of those features as we can.  
1. Migrate platform specific code to use Qt where possible
    - QStrings over platform native strings
    - QtDus in place of libportal for portals 
    - Qt classes in place of our in project created ones
    - QCommandLineOption / Parsing in place of CLI11
1. Only one instances of any given deskflow app can run at a time. In addition we need to prevent some combinations. The following should not be possible to run at the same time:
    - 2x `deskflow-client`
    - 2x `deskflow-server`
    - 2x `deskflow-core`,
    - 2x `deskflow-daemon`
    - 2x `deskflow-gui` (DONE)
    - `deskflow-client` and `deskflow-server` A machine is either a client or a server
    - `deskflow-core` and `deskflow-server` or `deskflow-client` When deskflow-core it is the exclusive client or server 

## Long Term Goals: 
 1.  separate the code into a set of common libraries that others can use to ensure compatibility and our own code that makes deskflow special. Other projects perhaps compositors would use this to add these features at a lower level or A display manager could for instance link the need items to allow connection to a server when before login. Deskflow and forks would ideally also use and develop these together

### Old Goals
These were our previous goals.

1. We will implement Wayland support with [libei](https://gitlab.freedesktop.org/libinput/libei)
1. The GUI source code will be migrated gradually from `/src/gui/src` to `/src/lib/gui` and `/src/cmd/deskflow`
1. GUI member variable names will be migrated gradually from pascal case (`m_Socket`) to camel case (`m_socket`)
    - Caveat: The whole class must use the same style, so the change should be all or nothing (within each class).
    - The rule for pointers is still the same; e.g. `m_pSocket`
1. The daemon (`deskflowd`) will be rewritten in Rust and will be cross-platform:
    - It will simply a watchdog for the client/server.
    - IPC will be done over Unix sockets instead of TCP (Windows now has `AF_UNIX`).
