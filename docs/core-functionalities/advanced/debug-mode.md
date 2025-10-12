# Debug Mode

This topic deals with the debug mode of battleWarden allowing you to provide the community useful information when
experiencing any issues and seeking for help. Usually the debug mode is disabled as it slows down the network
communication with your game server. However, if you find any bugs in battleWarden, activate the debug mode by
editing `settings.ini` file as shown below:

```ini title="settings.ini" hl_lines="2"
[General]
DebugMode = 1
AutoRefreshEnable = 1
AutoRefreshTime = 30
ReConnectDelay = 2
NetworkModule = 0
AdminName = SuperAdmin
```

After restarting battleWarden, it will create a log file called debug.log in the main application directory and keep
updating it. Please send us the file attached to a email when reporting any bugs.
