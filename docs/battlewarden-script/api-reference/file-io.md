# File IO

This module enables you to perform IO operations on files such as reading existing files and creating new ones.

---

## Functions

### `OpenFile(fileName as string) as integer`

**Description:**  
Opens an existing file for IO operations or creates a new file if it does not exist.

**Parameters:**  
- `fileName`: specifies the name of the file to be opened.

**Return Value:**  
- handle (integer) of the opened file. Will be `0` if the file could not be opened.

---

### `CreateFile(fileName as string) as integer`

**Description:**  
Creates a new file for writing operations.

**Parameters:**  
- `fileName`: specifies the name of the file to be created.

**Return Value:**  
- handle (integer) of the created file. Will be `0` if the file could not be created.

---

### `ReadFile(fileName as string) as integer`

**Description:**  
Opens an existing file for reading operations.

**Parameters:**  
- `fileName`: specifies the name of the file to be opened for reading.

**Return Value:**  
- handle (integer) of the opened file. Will be `0` if the file could not be opened for reading.

---

### `CloseFile(fileID as integer) as void`

**Description:**  
Closes a file and frees its resources.

**Parameters:**  
- `fileID`: specifies the handle of a previously opened or created file.

**Return Value:**  
- none

---

### `EndOfFile(fileID as integer) as integer`

**Description:**  
Checks whether the end of the file (EOF) has been reached (for reading purposes).

**Parameters:**  
- `fileID`: specifies the handle of a previously opened file.

**Return Value:**  
- `1` (true) if EOF has been reached, `0` (false) otherwise.

---

### `FileLength(fileID as integer) as integer`

**Description:**  
Returns the length of the file (LOF) in bytes.

**Parameters:**  
- `fileID`: specifies the handle of a previously opened or created file.

**Return Value:**  
- integer value specifying the length of the file in bytes.

---

### `FileSeek(fileID as integer, position as integer) as void`

**Description:**  
Changes the position for IO operations of a previously opened file.

**Parameters:**  
- `fileID`: specifies the handle of a previously opened or created file.  
- `position`: specifies a new position (in Byte) within the file (absolute position).

**Return Value:**  
- none

---

### `WriteString(fileID as integer, text as string) as void`

**Description:**  
Writes a string terminated by a new line to a previously opened or created file.

**Parameters:**  
- `fileID`: specifies the handle of a previously opened or created file.  
- `text`: specifies a string to be written to the file.

**Return Value:**  
- none

---

### `WriteInteger(fileID as integer, value as integer) as void`

**Description:**  
Writes an integer value to a previously opened or created file.

**Parameters:**  
- `fileID`: specifies the handle of a previously opened or created file.  
- `value`: specifies an integer value to be written to the file.

**Return Value:**  
- none

---

### `WriteFloat(fileID as integer, value as float) as void`

**Description:**  
Writes a float value to a previously opened or created file.

**Parameters:**  
- `fileID`: specifies the handle of a previously opened or created file.  
- `value`: specifies a float value to be written to the file.

**Return Value:**  
- none

---

### `ReadString(fileID as integer) as string`

**Description:**  
Reads a new line from a previously opened file.

**Parameters:**  
- `fileID`: specifies the handle of a previously opened or created file.

**Return Value:**  
- string specifying a new line read from the file.

---

### `ReadInteger(fileID as integer) as integer`

**Description:**  
Reads an integer value from a previously opened file.

**Parameters:**  
- `fileID`: specifies the handle of a previously opened or created file.

**Return Value:**  
- integer value read from the file.

---

### `ReadFloat(fileID as integer) as float`

**Description:**  
Reads a float value from a previously opened file.

**Parameters:**  
- `fileID`: specifies the handle of a previously opened or created file.

**Return Value:**  
- float value read from the file.

---

## Example Usage

```
; This sample demonstrates some functions of the I/O runtime.

function export Main (parameter as string)
    dim file as integer
    dim n as integer
    
    ; Create our file
    file = CreateFile("myfile.txt")
    if file
      for n = 0 to 10
        WriteString(file, "Hello world! " + Str(n))
      next
      CloseFile(file)
    endif
    
    ; Read our file
    file = ReadFile("myfile.txt")
    if file
      
      while EndOfFile(file) = 0
        Debug ReadString(file)
      wend
      
      CloseFile(file)
    endif
endfunction
```
