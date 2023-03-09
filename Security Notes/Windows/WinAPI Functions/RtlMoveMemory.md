---
date-created: 23-02-2023 11:55
name: RtlMoveMemory
return-type: VOID
header: Wdm.h (Windows.h)
dll: Ntdll.dll
docs: "[MSDN](https://learn.microsoft.com/en-us/windows/win32/devnotes/rtlmovememory)"
---
Date created: 23-02-2023 11:55
Date modified: `= dateformat(this.file.mtime, "dd-MM-yyyy HH:mm")`

### Description
----
Copies the contents of source memory block to destination, supports overlapping source and destionation.

### Syntax
----
```c++
VOID RtlMoveMemory(
  _Out_       VOID UNALIGNED *Destination,
  _In_  const VOID UNALIGNED *Source,
  _In_        SIZE_T         Length
);

```

### Parameters
----
| Type   | Name        | Info | Description             |
| ------ | ----------- | ---- | ----------------------- |
| void*  | Destination | Out  | Pointer to destination  |
| void*  | Source      | In   | Pointer to source       |
| size_t | Length      | In   | Number of bytes to copy |

###  Return Value
----
None

### Examples
----

#malware