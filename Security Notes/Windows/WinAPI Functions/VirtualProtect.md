---
date-created: 23-02-2023 12:04
name: VirtualProtect
return-type: BOOL
header: memoryapi.h (Windows.h)
dll: Kernel32.dll
docs: "[MSDN](https://learn.microsoft.com/en-us/windows/win32/api/memoryapi/nf-memoryapi-virtualalloc)"
---
Date created: 23-02-2023 12:04
Date modified: `= dateformat(this.file.mtime, "dd-MM-yyyy HH:mm")`

### Description
----
Change protection on memory region in virutal address space if the calling process.

### Syntax
----
```c++
BOOL VirtualProtect(
  _In_  LPVOID lpAddress,
  _In_  SIZE_T dwSize,
  _In_  DWORD  flNewProtect,
  _Out_ PDWORD lpflOldProtect
);
```

### Parameters
----
| Type   | Name                                               | Info | Description                |
| ------ | -------------------------------------------------- | ---- | -------------------------- |
| LPVOID | lpAddress                                          | in   | Pointer to memory address  |
| SIZE_T | dwSize                                             | in   | Length of memory in bytes  |
| DWORD  | [flNewProtect](Memory%20Protection%20Constants.md) | in   | Memory protection constant |
| PDWORD | lpflOldProtect                                     | out  | Pointer to a variable that recieves the old protection constant                           |

###  Return Value
----
Nonzero if success, zero if failure.

### Examples
----


#malware