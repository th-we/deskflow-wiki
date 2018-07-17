Some users prefer to use the command line to run Synergy instead of using automatic configuration.

General information
-------------------

The Synergy binaries generally take the same parameters on all 3
platforms.

See [[Text-Config]] for information on how to create a config file. If you
have another system on which you can use the GUI, you might consider
setting up your system in that GUI, and then exporting the config file
with File --&gt; Save Configuration As and copy it over to the system
you need it on. The same config file will work on any platform.

Synergy Core v1.x
-----------------

Open up a command prompt and cd into the Synergy install directory.

| OS | Command |
| ------- | --------------------------------------------- |
| Windows | `cd "C:\Program Files\Synergy"`               |
| macOS   | `cd /Applications/Synergy.app/Contents/Resources/` |
| Linux   | `cd /usr/bin`                                 |

Run the Synergy client binary, pointing it at the Synergy Server.

| OS | Command |
| ------- | ------------------------------------- |
| Windows | `synergyc [server IP]`   |
| macOS   | `./synergyc [server IP]` |
| Linux   | `./synergyc [server IP]` |

Run the Synergy server binary, pointing it at the configuration file.

| OS | Command |
| ------- | -------------------------------------------------- |
| Windows | `synergys -c [path to config file]`   |
| macOS   | `./synergys -c [path to config file]` |
| Linux   | `./synergys -c [path to config file]` |

Synergy Core v2.x
-----------------

Open up a command prompt and cd into the Synergy install directory.

| OS | Command |
| ------- | --------------------------------------------- |
| Windows | `cd "C:\Program Files\Synergy"`               |
| macOS   | `cd /Applications/Synergy.app/Contents/Resources/` |
| Linux   | `cd /usr/bin`                                 |

Run the Synergy client binary, pointing it at the Synergy Server.

| OS | Command |
| ------- | ------------------------------------- |
| Windows | `synergy-core --client [server IP]`   |
| macOS   | `./synergy-core --client [server IP]` |
| Linux   | `./synergy-core --client [server IP]` |

Run the Synergy server binary, pointing it at the configuration file.

| OS | Command |
| ------- | -------------------------------------------------- |
| Windows | `synergy-core --server -c [path to config file]`   |
| macOS   | `./synergy-core --server -c [path to config file]` |
| Linux   | `./synergy-core --server -c [path to config file]` |

Command line options
--------------------

  [Text Config]: Text_Config "wikilink"

### Options for `synergy-core --client`

Taken from MacOS X 10.11 system:

```
Usage: synergy-core --client [--yscroll <delta>] [--daemon|--no-daemon] [--name <screen-name>] [--restart|--no-restart] [--debug <level>] <server-address>

Connect to a synergy mouse/keyboard sharing server.

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

Unlike `synergy-core --server`, `synergy-core --client` has no config file.
The options are set either at runtime by the command line on the client,
or for settings inherited from Synergy server they are set at connection time.

## Options for `synergy-core --server`

Taken from a MacOS X 10.11 system:
```
Usage: synergy-core --server [--address <address>] [--config <pathname>] [--daemon|--no-daemon] [--name <screen-name>] [--restart|--no-restart] [--debug <level>]

Start the synergy mouse/keyboard sharing server.

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
  $HOME/.synergy.conf
  /etc/synergy.conf
```
