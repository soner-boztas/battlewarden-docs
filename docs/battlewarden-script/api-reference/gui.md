# GUI

Manipulating the graphical user interface of battleWarden is accomplished using the GUI module.

---

## Functions

### `Debug(message as string) as void`

**Description:**  
Writes a message terminated with a new line to the Script log of the battleWarden GUI.

**Parameters:**  
- `message`: specifies the message to be printed.

**Return Value:**  
- none

---

### `SetStatusBarText(text as string) as void`

**Description:**  
Displays a text in the status bar of the battleWarden GUI.

**Parameters:**  
- `text`: specifies the text to be displayed.

**Return Value:**  
- none

---

### `PopUpSysTrayInfo(title as string, message as string) as void`

**Description:**  
Displays a popup window in the system tray.

**Parameters:**  
- `title`: specifies the title of the systray popup window.  
- `message`: specifies the message of the systray popup window.

**Return Value:**  
- none

---

## Example Usage

```
function export Main (parameter as string)
    ; Will be printed in the "Script" tab in the battleWarden GUI.
    Debug "==================== Hello world! ===================="
    
    ; Will be printed in the "Log" tab in the battleWarden GUI.
    LogOutput "==================== Hello world! ===================="
endfunction
```
