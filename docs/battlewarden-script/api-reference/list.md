# List

Lists serve as a simple container mechanism for managing ordered collections of tables within scripts.

Because the scripting language used by battleWarden (battleScript) does not have built-in dynamic lists,
this module provides a minimal runtime implementation of a linked list that stores table pointers.

---

## Functions

### `CreateList() as integerptr`

**Description:**  
Creates a new list by allocating memory.

**Parameters:**

- *none*

**Return Value:**

- pointer to the created list (`integerptr`)

---

### `FreeList(list as integerptr) as void`

**Description:**  
Frees an existing list by deallocating its memory.

**Parameters:**

- `list`: specifies a pointer to an existing list.

**Return Value:**

- *none*

---

### `ListSize(list as integerptr) as integer`

**Description:**  
Returns the number of tables that have been added to the list.

**Parameters:**

- `list`: specifies a pointer to an existing list.

**Return Value:**

- number of tables within the list.

---

### `ClearList(list as integerptr) as void`

**Description:**  
Removes all tables from the specified list.  
The list itself will not be deleted.

**Parameters:**

- `list`: specifies a pointer to an existing list.

**Return Value:**

- *none*

---

### `AddTable(list as integerptr, table as integerptr) as void`

**Description:**  
Adds an existing table to the end of the specified list.

**Parameters:**

- `list`: specifies a pointer to an existing list.
- `table`: specifies a pointer to an existing table.

**Return Value:**

- *none*

---

### `GetTable(list as integerptr) as integerptr`

**Description:**  
Returns the current table stored in the list.

**Parameters:**

- `list`: specifies a pointer to an existing list.

**Return Value:**

- pointer to the current table.

---

### `RemoveTable(list as integerptr) as void`

**Description:**  
Removes the current table stored in the list.

**Parameters:**

- `list`: specifies a pointer to an existing list.

**Return Value:**

- *none*

---

### `ResetListIteration(list as integerptr) as void`

**Description:**  
Resets the iteration of the specified list and jumps **before** the first table.  
After calling this function, you must use `nexttable` before calling `gettable`.

**Parameters:**

- `list`: specifies a pointer to an existing list.

**Return Value:**

- *none*

---

### `NextTable(list as integerptr) as integerptr`

**Description:**  
Jumps to the next list element.

**Parameters:**

- `list`: specifies a pointer to an existing list.

**Return Value:**

- pointer to the next list element.
- returns `0` if there is no next element.

---

## Example Usage

```
function export Main (parameter as string)
    dim n as integer
    dim file as integer
    dim table as integerptr
    dim list as integerptr
    
    ; Note: Our working directory is still the main application directory of battleWarden and not the directory the script file is located in.
    file = ReadFile("Scripts\Samples\List\list.txt") 
    if file
    
      list = CreateList()
      
      while EndOfFile(file) = 0
        table = CreateTable() ; Create a new table.
        
        for n = 0 to 2
          SetString(table, Str(n), ReadString(file))
        next
        
        AddTable(list, table) ; Add the created table to our list.
      wend
    
    
      ResetListIteration(list) ; Make our list jump before the first table. So there is no current table.
      
      ; NextTable will jump to the next table within our list.
      ; The first time this function is called, our list will jump to the first element and not the second one because of ResetListIteration!
      while NextTable(list) <> 0 
        table = GetTable(list) ; Get the current table in our list.
        
        Debug GetString(table, "0")
        Debug GetString(table, "1")
        Debug GetString(table, "2")
        
        FreeTable(table) ; Delete the current table to free memory.
      wend
    
      FreeList(list)
    
      CloseFile(file)
    endif
endfunction
```
