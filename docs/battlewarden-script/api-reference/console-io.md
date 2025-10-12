# Console IO

The console module provides basic functions for IO operations on the stdin and stdout of battleWarden.

---

## Functions

### `OpenConsole(title as string) as void`

**Description:**  
Opens the console for IO operations.

**Parameters:**  
- `title`: specifies the title of the console.

**Return Value:**  
- none

---

### `Print(text as string) as void`

**Description:**  
Writes a string terminated with a new line to stdout.

**Parameters:**  
- `text`: specifies the text to be printed.

**Return Value:**  
- none

---

### `Input() as string`

**Description:**  
Reads a string from the stdin.

**Parameters:**  
- none

**Return Value:**  
- string read from stdin.

---

## Example Usage

```
; This sample demonstrates some functions of the console runtime.

function export Main (parameter as string)
    dim str as string
    
    ConsoleOpen("Title")
    
    str = Input()
    
    Print("You entered: " + str)
    Print("Please hit return in order to close the console.")
    
    Input()
    
    ConsoleClose()
endfunction
```
