# Configuring Triggers

Triggers being part of battleWarden:Spy allow you to catch any kind of message battleWarden receives from your game
server and perform a custom action. Triggers are created within the nested class `Triggers` in the battleWarden:Spy
configuration file. To accomplish this, add a new nested class with a user-defined name (here: `trigger0`) as shown in
the example below:

```cpp title="bwspysettings.ini" hl_lines="8 9 10 11 12 13 14"
class bWSpySettings{

class Log{
    // ...
}

class Triggers{
    class trigger0{
        Type="Log"
        Pattern="logged in"
        Call=""
        Sound="Resources\drum.wav"
        Script = "Scripts\TriggerScripts\loggedIn.bs"
    }

}

// ...
```

Each custom trigger nested class has 4 attributes:

| Attribute | Description                                                                                                                                                                                                                                             |
|-----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Type`    | Specifies the type of the messages to be caught. Values can be `Log` (for log messages) or `Chat` (for chat messages).                                                                                                                                  |
| `Pattern` | Specifies a regular expression for catching server messages.                                                                                                                                                                                            |
| `Call`    | Specifies a web URI to call when catching a message. You can use `<Base64Content>` as a variable containing the caught message encoded with Base64. This attribute can be empty.                                                                        |
| `Sound`   | Specifies a `.wav` sound file to be played when catching a message.                                                                                                                                                                                     |
| `Script`  | Specifies a path to a battleWarden script file which will be executed when catching a message. Within that script you have to define a function called `Main` with 1 parameter of the type `string`. For detailed information, see battleWarden:Script. |

You can add an unlimited number of custom triggers. Please make sure that each of these triggers have an individual
name (like `trigger0`, `trigger1`, ...) in order to avoid collisions.

!!! tip

    Alternatively, you can configure custom triggers by using the settings dialog (click `Settings` --> `Settings...`)
    in the [Main Menu Bar]).

[Main Menu Bar]: ../core-functionalities/basic/overview-main-application-window.md

