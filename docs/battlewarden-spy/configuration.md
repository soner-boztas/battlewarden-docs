# Configuration

Configuring battleWarden:Spy is simple and conducted via the `bwspysettings.ini` file located in the root
application directory.

!!! note

    Although the extension of the file is `ini`, it is not a conventional `ini` file. The content of the settings file
    exhibits a more complex structure and follows a declarative syntax composed of (nested) classes and attributes. 

The general structure of the `bwspysettings.ini` file looks as follows:

```cpp title="bwspysettings.ini"
class bWSpySettings{

    class Log{
        // Definition of attributes of the nested Log class.
    }
    
    class Triggers{
        // Definition of nested trigger classes.
    }

}
```

`bWSpySettings` is the main configuration class, which does not have any attributes. Instead, it consists of the 2
nested configuration classes `Log` and `Triggers`, through which logs and custom triggers are set up.

A possible configuration would look like this:

```cpp title="bwspysettings.ini"
class bWSpySettings{

  class Log{
    Enable = "1"
    LogPath = "Logs\"
    FileMask = "<ServerDescription>_<Date>_<Type>.txt"
    DateMask = "%yyyy-%mm-%dd"
    TimeMask = "(%hh:%ii:%ss) :"
  }
  
  class Triggers{
    class trigger0{
      Type = "Chat"
      Pattern = "!admin"
      Call = ""
      Sound = ""
      Script = "Scripts\TriggerScripts\callAdmin.bs"
    }
  }
  
}
```

!!! tip

    Alternatively, you can configure battleWarden:Spy by using the settings dialog
    (click `Settings` --> `Settings...` in the [Main Menu Bar]).

[Main Menu Bar]: ../core-functionalities/basic/overview-main-application-window.md
