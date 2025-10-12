# Server

The server module gives you access to the core functionality of battleWarden by enabling you to communicate with a
game server that supports [BattlEye].

---

## Functions

### `Connect(host as string, port as integer, password as string) as integer`

**Description:**  
Connects to a [BattlEye] server.

**Parameters:**

- `host`: specifies the host name or IP address of the server to connect to.
- `port`: specifies the port of the server to connect to.
- `password`: specifies the password of the server to connect to.

**Return Value:**

- `1` if succeeded, otherwise `0`.

---

### `Disconnect() as void`

**Description:**  
Disconnects from the current [BattlEye] server.

**Parameters:**

- none

**Return Value:**

- none

---

### `BESendCommand(command as string) as void`

**Description:**  
Sends a command to the [BattlEye] server that battleWarden is currently connected to.  
See [BattlEye RCon protocol](https://community.bistudio.com/wiki/BattlEye) for more information.

**Parameters:**

- `command`: specifies the BattlEye command.

**Return Value:**

- none

---

### `BEGetBanList() as integer`

**Description:**  
Receives the complete ban list and prepares it for examination.

**Parameters:**

- none

**Return Value:**

- number of bans.

---

### `BENextBanListElement() as integer`

**Description:**  
Moves the current ban entry to the next one in the list.  
You should call `BEGetBanList()` before using this command.

**Parameters:**

- none

**Return Value:**

- `1` if another ban entry exists, otherwise `0`.

---

### `BEGetCurrentBanID() as string`

**Description:**  
Returns the ID (GUID or IP) of the current ban entry.

**Parameters:**

- none

**Return Value:**

- ID (GUID or IP) of the current ban entry.

---

### `BEGetCurrentBanDuration() as string`

**Description:**  
Returns the duration of the current ban entry.

**Parameters:**

- none

**Return Value:**

- duration of the current ban entry.

---

### `BEGetCurrentBanReason() as string`

**Description:**  
Returns the reason for the current ban entry.

**Parameters:**

- none

**Return Value:**

- reason of the current ban entry.

---

### `BEGetPlayerList() as integer`

**Description:**  
Retrieves the complete player list and prepares it for examination.

**Parameters:**

- none

**Return Value:**

- number of active clients or players on the server.

---

### `BENextPlayerListElement() as integer`

**Description:**  
Moves the current player entry to the next one in the list.  
You should call `BEGetPlayerList()` before using this command.

**Parameters:**

- none

**Return Value:**

- `1` if another player entry exists, otherwise `0`.

---

### `BEGetCurrentPlayerName() as string`

**Description:**  
Returns the name of the current player entry.

**Parameters:**

- none

**Return Value:**

- name of the current player entry.

---

### `BEGetCurrentPlayerScore() as integer`

**Description:**  
Reserved for future use.

**Parameters:**

- none

**Return Value:**

- score of the current player entry.

---

### `BEGetCurrentPlayerDeaths() as integer`

**Description:**  
Reserved for future use.

**Parameters:**

- none

**Return Value:**

- number of deaths of the current player entry.

---

### `BEGetCurrentPlayerTeam() as integer`

**Description:**  
Reserved for future use.

**Parameters:**

- none

**Return Value:**

- team name of the current player entry.

---

### `BEGetCurrentPlayerPing() as integer`

**Description:**  
Returns the ping of the current player entry.

**Parameters:**

- none

**Return Value:**

- ping of the current player entry.

---

### `BEGetCurrentPlayerIP() as string`

**Description:**  
Returns the IP address of the current player entry.

**Parameters:**

- none

**Return Value:**

- IP of the current player entry.

---

## Example Usage

```
; This sample will go through all players and display them in a console.
; !!!!!!!!!!!!!!!!!!!! IMPORTANT NOTE !!!!!!!!!!!!!!!!!!!!
; This code can take a few seconds to finish.

function export Main (parameter as string)
    dim playerCount as integer
    
    ConsoleOpen("Players")
    
    playerCount = BEGetPlayerList()
    
    while BENextPlayerListElement()
      Print(BEGetCurrentPlayerName() + " : " + BEGetCurrentPlayerIP())
    wend
    
    Print("Total player count: " + Str(playerCount))
    
    Print("Please hit return in order to close the console.")
    
    Input()
    
    ConsoleClose()
endfunction
```
