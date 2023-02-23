---
date-created: 21-02-2023 18:12
name: VirtualAlloc
return-type: LPVOID
header: memoryapi.h (Windows.h)
dll: Kernel32.dll
docs: "[MSDN](https://learn.microsoft.com/en-us/windows/win32/api/memoryapi/nf-memoryapi-virtualalloc)"
---

Date created: 21-02-2023 18:12
Date modified: `= dateformat(this.file.mtime, "dd-MM-yyyy HH:mm")`

### Description
----
Reserves a memory location in the virtual address space of the current process and returns a pointer to the beginning of the location. Automatically initiates the memory to zero.


### Syntax
----
```c++
LPVOID VirtualAlloc(
  _In_, _Optional_ LPVOID lpAddress,
  _In_             SIZE_T dwSize,
  _In_             DWORD  flAllocationType,
  _In_             DWORD  flProtect
);
```

### Parameters
----
| Type   | Name             | Info         | Description                                   |
| ------ | ---------------- | ------------ | --------------------------------------------- |
| LPVOID | lpAddress        | in, optional | Starting address of region to allocate        |
| SIZE_T | dwSize           | in           | Size of region to allocate in bytes           |
| DWORD  | [[flAllocationType]] | in           | Type of memory allocation                     |
| DWORD  | [flProtect](Memory%20Protection%20Constants.md)        | in           | Type of memory protection (read, write, etc.) |

###  Return Value
----
Addres to memory if success, NULL if failure.

### Examples
```cpp
void* code_mem = VirtualAlloc(0, payload_len, MEM_COMMIT | MEM_RESERVE, PAGE_READ_WRITE);
```

