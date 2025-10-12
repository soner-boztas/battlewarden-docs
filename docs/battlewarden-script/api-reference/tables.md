# Tables

This section describes the API functions for managing table objects in the battleWarden scripting environment.  
Tables act as associative containers that can store and retrieve string or integer values by key.

---

## Functions

### `CreateTable() as integerptr`

**Description:**  
Creates a new table by allocating memory.

**Parameters:**  
- *none*

**Return Value:**  
- **Pointer** to the created table (`integerptr`).

---

### `FreeTable(table as integerptr) as void`

**Description:**  
Frees an existing table by deallocating its memory.

**Parameters:**  
- `table`: Pointer to an existing table.

**Return Value:**  
- *none*

---

### `SetInteger(table as integerptr, key as string, value as integer) as void`

**Description:**  
Adds or updates an integer value in an existing table under the specified key.  
If a key with the same name already exists, the existing value will be replaced.

**Parameters:**  
- `table`: Pointer to an existing table.  
- `key`: Identifier (string) for the value to be stored.  
- `value`: Integer value to store.

**Return Value:**  
- *none*

---

### `SetString(table as integerptr, key as string, value as string) as void`

**Description:**  
Adds or updates a string value in an existing table under the specified key.  
If a key with the same name already exists, the existing value will be replaced.

**Parameters:**  
- `table`: Pointer to an existing table.  
- `key`: Identifier (string) for the value to be stored.  
- `value`: String value to store.

**Return Value:**  
- *none*

---

### `GetInteger(table as integerptr, key as string) as integer`

**Description:**  
Retrieves the integer value associated with the specified key in the given table.  
If the key does not exist, the function returns `0`.

**Parameters:**  
- `table`: Pointer to an existing table.  
- `key`: Identifier for the desired value.

**Return Value:**  
- Integer value of the specified key, or `0` if not found.

---

### `GetString(table as integerptr, key as string) as string`

**Description:**  
Retrieves the string value associated with the specified key in the given table.  
If the key does not exist, the function returns an empty string.

**Parameters:**  
- `table`: Pointer to an existing table.  
- `key`: Identifier for the desired value.

**Return Value:**  
- String value of the specified key, or an empty string if not found.

---

## Example Usage

```
function export Main (parameter as string)
  dim table as integerptr
  
  table = CreateTable() ; Create a new table.
  
  SetInteger(table, "key1", 1) ; Create a new value with its associated key.
  SetInteger(table, "key2", 2)
  SetString(table, "key3", "I am a string but will be replaced!")
  SetString(table, "key3", "I am a string!") ; Replace string of key3 with a new string.
    
  Debug Str(GetInteger(table, "key1"))
  Debug Str(GetInteger(table, "key2"))
  Debug GetString(table, "key3")
  
  Debug GetString(table, "key4") ; Will return an empty string as the key does not exist.
  
  FreeTable(table) ; NEVER forget deleting your tables to free the memory.
  
endfunction
```
