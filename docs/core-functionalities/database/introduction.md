# Introduction

As long as battleWarden stays connected to a game server, it will collect data about its clients/players including the
following data:

- Player name
- Player IP
- [BattlEye] GUID
- The name of your server the player is connected to
- Date of the last connection ([ISO format](https://en.wikipedia.org/wiki/ISO_8601))

This is one of the most powerful features supported by battleWarden and will not only support you in detecting
cheaters/hackers but also create useful statistics for your game servers.

The collected data is stored in a simple, [SQLite] database on your local machine and can be found
in `%APPDATA%\battleWarden\db.db`.
