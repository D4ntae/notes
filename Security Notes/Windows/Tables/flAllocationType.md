
| Typedef         | Code       | Description                                                                            |
| --------------- | ---------- | -------------------------------------------------------------------------------------- |
| MEM_COMMIT      | 0x00001000 | Actually allocates the physical memory, often used with MEM_RESERVE                    |
| MEM_RESERVE     | 0x00002000 | Reserves memory but doesn't allocate it. Memory must be first reserved then allocated. |
| MEM_RESET       | 0x00080000 | Signals the memory is currently not of interest but might be used in the future        |
| MEM_RESET_UNDO  | 0x10000000 | Undos MEM_RESET                                                                        |
| MEM_LARGE_PAGES | 0x20000000 | Allocates using large page support                                                     |
| MEM_PHYSICAL    | 0x00400000 | Reserves a range that can be used to map AWE pages                                     |
| MEM_TOP_DOWN    | 0x00100000 | Allocates at highest possible memory                                                   |
| MEM_WRITE_WATCH | 0x00200000 | Causes the system to track the memory region                                           |
