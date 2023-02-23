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
```cpp
LPVOID VirtualAlloc(
  [in, optional] LPVOID lpAddress,
  [in]           SIZE_T dwSize,
  [in]           DWORD  flAllocationType,
  [in]           DWORD  flProtect
);
```

### Parameters
----
| Return | Name      | Info         | Description |
| ------ | --------- | ------------ | ----------- |


### Examples


