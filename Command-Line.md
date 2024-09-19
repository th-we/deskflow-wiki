Some users prefer to use the command line to run Deskflow instead of using automatic configuration.

General information
-------------------

The Deskflow binaries generally take the same parameters on all 3
platforms.

See [[Text-Config]] for information on how to create a config file. If you
have another system on which you can use the GUI, you might consider
setting up your system in that GUI, and then exporting the config file
with File --&gt; Save Configuration As and copy it over to the system
you need it on. The same config file will work on any platform.

Open up a command prompt and cd into the Deskflow install directory.

| OS | Command |
| ------- | --------------------------------------------- |
| Windows | `cd "C:\Program Files\Deskflow"`               |
| macOS   | `cd /Applications/Deskflow.app/Contents/Resources/` |
| Linux   | `cd /usr/bin`                                 |

Run the Deskflow client binary, pointing it at the Deskflow Server.

| OS | Command |
| ------- | ------------------------------------- |
| Windows | `deskflowc [server IP]`   |
| macOS   | `./deskflowc [server IP]` |
| Linux   | `./deskflowc [server IP]` |

Run the Deskflow server binary, pointing it at the configuration file.

| OS | Command |
| ------- | -------------------------------------------------- |
| Windows | `deskflows -c [path to config file]`   |
| macOS   | `./deskflows -c [path to config file]` |
| Linux   | `./deskflows -c [path to config file]` |

Command line options
--------------------

  [Text Config]: Text_Config "wikilink"

### Options for `deskflow-core --client`

Taken from MacOS X 10.11 system:

```
Usage: deskflowc [--address <address>] [--yscroll <delta>] [--daemon|--no-daemon] [--name <screen-name>] [--restart|--no-restart] [--debug <level>] <server-address>

Connect to a deskflow mouse/keyboard sharing server.

  -a, --address <address>  local network interface address.
  -d, --debug <level>      filter out log messages with priority below level.
                             level may be: FATAL, ERROR, WARNING, NOTE, INFO,
                             DEBUG, DEBUG1, DEBUG2.
  -n, --name <screen-name> use screen-name instead the hostname to identify
                             this screen in the configuration.
  -1, --no-restart         do not try to restart on failure.
*     --restart            restart the server automatically if it fails.
  -l  --log <file>         write log messages to file.
      --no-tray            disable the system tray icon.
      --enable-drag-drop   enable file drag & drop.
  -f, --no-daemon          run in the foreground.
*     --daemon             run as a daemon.
      --yscroll <delta>    defines the vertical scrolling delta, which is
                             120 by default.
  -h, --help               display this help and exit.
      --version            display version information and exit.

* marks defaults.

The server address is of the form: [<hostname>][:<port>].  The hostname
must be the address or hostname of the server.  The port overrides the
default port, 24800.
```

Unlike `deskflows`, `deskflowc` has no config file.
The options are set either at runtime by the command line on the client,
or for settings inherited from Synergy server they are set at connection time.

## Options for `deskflow-core --server`

Taken from a MacOS X 10.11 system:
```
Usage: deskflows [--address <address>] [--config <pathname>] [--daemon|--no-daemon] [--name <screen-name>] [--restart|--no-restart] [--debug <level>]

Start the deskflow mouse/keyboard sharing server.

  -a, --address <address>  listen for clients on the given address.
  -c, --config <pathname>  use the named configuration file instead.
  -d, --debug <level>      filter out log messages with priority below level.
                             level may be: FATAL, ERROR, WARNING, NOTE, INFO,
                             DEBUG, DEBUG1, DEBUG2.
  -n, --name <screen-name> use screen-name instead the hostname to identify
                             this screen in the configuration.
  -1, --no-restart         do not try to restart on failure.
*     --restart            restart the server automatically if it fails.
  -l  --log <file>         write log messages to file.
      --no-tray            disable the system tray icon.
      --enable-drag-drop   enable file drag & drop.
  -f, --no-daemon          run in the foreground.
*     --daemon             run as a daemon.
  -h, --help               display this help and exit.
      --version            display version information and exit.

* marks defaults.

The argument for --address is of the form: [<hostname>][:<port>].  The
hostname must be the address or hostname of an interface on the system.
The default is to listen on all interfaces.  The port overrides the
default port, 24800.

If no configuration file pathname is provided then the first of the
following to load successfully sets the configuration:
  $HOME/.deskflow.conf
  /etc/deskflow.conf
```
