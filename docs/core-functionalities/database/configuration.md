# Configuration

Configuring the database is quite simple and only needs the `settings.ini` file[^1] edited. After opening the
`settings.ini` file, change the value of `Enable` to `1` in the `Database` section as shown in the example below.
This will activate the database feature.

```ini title="settings.ini" hl_lines="9"
[General]
AutoRefreshEnable = 1
AutoRefreshTime = 30
ReConnectDelay = 2
NetworkModule = 0
AdminName = JohnDoe

[Database]
Enable = 1
```

After restarting battleWarden it will keep populating the database when connected to a game server.

!!! tip

    Alternatively, you can enable the database feature from the battleWarden user interface itself. In order to do so,
    click `Settings` --> `Settings...` in the [Main Menu Bar] Then, in the appearing `Settings`
    dialog window, switch to the `General` section and activate the `Enable Database` checkbox.

[^1]: Located in the root application folder of battleWarden.

[Main Menu Bar]: ../basic/overview-main-application-window.md
