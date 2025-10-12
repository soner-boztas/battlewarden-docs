# Configuring Logs

battleWarden is capable of creating logs of your game server messages. In order to configure the log
functionality, you will need to edit the` bwspysettings.ini` file located in the root application directory.
A simple text editor is suitable here. After opening the `byspysettings.ini` file you will notice a section that looks
like the following example:

```cpp title="bwspysettings.ini"
class bWSpySettings{

    class Log{
        Enable="1"
        LogPath="Logs\"
        FileMask="<ServerDescription>_<Date>_<Type>.txt"
        DateMask="%yyyy-%mm-%dd"
        TimeMask="(%hh:%ii:%ss) : "
    }
    
    // ...
```

The example shows the configuration class for the log functionality called `Log`, being a nested class
within `bWSpySettings`. To instruct battleWarden to log server messages, you need to set `Enable` to `1` as shown in the
above example. Then, you need to specify a path for the folder, where battleWarden will create the log files. This is
done by modifying the `LogPath` attribute. Please make sure that the specified path ends with a backslash character `\`.
battleWarden will use the file mask specified for the `FileMask` attribute as the name for the logs files.
The following variables can be used for the `FileMask`:

| Variable              | Description                                                                                            |
|-----------------------|--------------------------------------------------------------------------------------------------------|
| `<ServerDescription>` | Contains the description of the game server battleWarden is connected to.                              |
| `<Date>`              | Contains the current system date formatted with the mask specified in the DateMask parameter.          |
| `<Type>`              | Contains the type of the current server message to be logged in form of a string (either Log or Chat). |

The `DateMask` attribute specifies a mask battleWarden will use to format the current system date. It is used for the
explained <Date> variable. When logging server messages, battleWarden uses a prefix for each message specifying the
time. This prefix has to be specified in the `TimeMask` attribute containing a mask for formatting the current system
time.

!!! tip

    Alternatively, you can configure logs by using the settings dialog (click `Settings` --> `Settings...`)
    in the [Main Menu Bar]).

[Main Menu Bar]: ../core-functionalities/basic/overview-main-application-window.md
