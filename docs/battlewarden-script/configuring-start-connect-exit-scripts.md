# Configuring Start/Connect/Exit Scripts

battleWarden allows you to configure scripts for the following *special application events*:

* battleWarden is launched
* battleWarden connects to a server
* battleWarden exits

I.e. when one of those events occur, you are able to instruct battleWarden to execute scripts.

Configuring scripts for *special application events* is conducted in the `bwscriptsettings.ini` located in the
battleWarden root application directory. The settings file consists of a class `bWScriptSettings` as shown in the
example below:

```cpp
class bWScriptSettings{
    StartScript="Scripts\start.bs"
    ConnectScript="Scripts\connect.bs"
    ExitScript="Scripts\exit.bs"
}
```

Within this base class, you have to define the following 3 attributes:

| Variable          | Description                                                                       |
|-------------------|-----------------------------------------------------------------------------------|
| `<StartScript>`   | Specifies the path of the script file to be executed when starting battleWarden.  |
| `<ConnectScript>` | Specifies the path of the script file to be executed when connecting to a server. |
| `<ExitScript>`    | Specifies the path of the script file to be executed when exiting battleWarden.   |

Within the specified script files you have to define a function called `Main` taking a dummy parameter of the type
`string`. This function will be called when executing the scripts.
