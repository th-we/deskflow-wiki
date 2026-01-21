Some users prefer to use the command line to run Deskflow instead of using automatic configuration.

General information
-------------------

The Deskflow binaries generally take the same parameters on all 3
platforms.

See [Text-Config](https://github.com/deskflow/deskflow/wiki/Server-Text-Config) for information on how to create a config file. If you
have another system on which you can use the GUI, you might consider
setting up your system in that GUI, and then exporting the config file
with File --&gt; Save Configuration As and copy it over to the system
you need it on. The same config file will work on any platform.

Open up a command prompt and cd into the Deskflow install directory.

| OS | Command |
| ------- | --------------------------------------------- |
| Windows | `cd "C:\Program Files\Deskflow"`               |
| macOS   | `cd /Applications/Deskflow.app/Contents/MacOS/` |
| Linux   | `cd /usr/bin`                                 |

Run the Deskflow core in client mode, pointing it at the Deskflow Server.

| OS | Command |
| ------- | ------------------------------------- |
| Windows | `deskflow-core client [server IP]`   |
| macOS   | `./deskflow-core client [server IP]` |
| Linux   | `./deskflow-core client [server IP]` |

Run the Deskflow core in server mode, pointing it at the configuration file.

| OS | Command |
| ------- | -------------------------------------------------- |
| Windows | `deskflow-core server -s [path to settings file]`   |
| macOS   | `./deskflow-core server -s [path to settings file]` |
| Linux   | `./deskflow-core server -s [path to settings file]` |

Command line options
--------------------

  [Text Config]: Text_Config "wikilink"

### Options for `deskflow-core`

```
❯ deskflow-core --help
deskflow-core: 1.25.0.23 (7e278b62)
Usage: deskflow-core coremode [options]
Keyboard and mouse sharing utility

Options:
  -h, --help                   Display Help on the command line
  -v, --version                Display version information
  --new-instance               Skip the check for a running instance, always
                               makes a new instance
  -s, --settings <configFile>  override configuration file to use

Arguments:
  coremode                     The mode to start in either: server or client
```
