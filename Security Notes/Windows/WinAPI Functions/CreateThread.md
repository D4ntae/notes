---
date-created: 23-02-2023 13:44
name: CreateThread
return-type: HANDLE
header: processthreadapi.h (Windows.h)
dll: Kernel32.dll
docs: "[MSDN](https://learn.microsoft.com/en-us/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)"
---
Date created: 23-02-2023 13:44
Date modified: `= dateformat(this.file.mtime, "dd-MM-yyyy HH:mm")`

### Description
----
Creates a thread to execute in the virtual address space of the calling process.

### Syntax
----
```c++
HANDLE CreateThread(
  [in, optional]  LPSECURITY_ATTRIBUTES   lpThreadAttributes,
  [in]            SIZE_T                  dwStackSize,
  [in]            LPTHREAD_START_ROUTINE  lpStartAddress,
  [in, optional]  __drv_aliasesMem LPVOID lpParameter,
  [in]            DWORD                   dwCreationFlags,
  [out, optional] LPDWORD                 lpThreadId
);
```

### Parameters
----
| Type                   | Name               | Info          | Description                                                                                               |
| ---------------------- | ------------------ | ------------- | --------------------------------------------------------------------------------------------------------- |
| LPSECURITY_ATTRIBUTES  | lpThreadAttributes | in, optional  | Determines whether the returned handle can be inherited by a child process. If NULL it can't be inherited |
| SIZE_T                 | dwStackSize        | in            | Initial size of the stack in bytes. If 0 use process default                                              |
| LPTHREAD_START_ROUTINE | lpStartAddress     | in            | Pointer to application-defined function to be executed in the thread.                                     |
| LPVOID                 | lpParameter        | in, optional  | A pointer to a variable to be passed to the thread.                                                       |
| DWORD                  | dwCreationFlags    | in            | Flags that control creation of the thread. 0 - run immediately, CREATE_SUSPENDED - suspended.             |
| LPDWORD                | lpThreadId         | out, optional | Pointer to a variable that recieves the thread identifier.                                                                                                          |

###  Return Value
----
Handle to thread if success, NULL if failure.

### Examples
----


#malware