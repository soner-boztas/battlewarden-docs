# Process

The process module provides a small API for running external processes on the operating system.

---

## Functions

### `RunProcess(programName as string, parameter as string, workingDirectory as string, flags as string) as void`

**Description:**  
Runs a new process.

**Parameters:**  
- `programName`: name of the process to run.  
- `parameter`: command-line parameters to be passed to the program.  
- `workingDirectory`: working directory of the running program.  
- `flags`: can contain `"-wait"` (waits until the program exits) and `"-hide"` (starts the program in hidden mode).

**Return Value:**  
- none

---

## Example Usage

```
; Sample demonstrating the RunProcess function.
; 1. Parameter (string): Process name
; 2. Parameter (string): Command-line arguments
; 3. Parameter (string): Working directory
; 4. Parameter (string): Flags (combination of -hide and -wait)

function export Main (parameter as string)
    RunProcess("cmd.exe", "", "", "")
endfunction
```
