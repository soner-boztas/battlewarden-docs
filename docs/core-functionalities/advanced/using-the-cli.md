# Using the CLI

battleWarden supports a command-line interface (CLI) enabling you to run the application with command-line parameters.
Using the `/c` parameter followed by a string specifying the description of a game server as contained in the server
manager will make battleWarden connect to that server immediately after launch.

The following example will make battleWarden connect to `myGameServer`. Please make sure that there is a game server
with the description `myGameServer` contained in your server manager.

## Example

```
battleWarden /c myGameServer
```
