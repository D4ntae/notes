---
date-created: 23-02-2023 14:38
platform: Windows
language: C (AutoIT)
tools: autoit-ripper, x32dbg
solved: 1
---

### Notes
----
- File was an AutoIT script
- To extract the script part from exe use autoit-ripper
- Couldn't debug with x32dbg

### Writeup
----
The file is a AutoIt script as indicated in the description but you can also figure that out if you try to debug it with x32dbg as it will throw this error.
![[Pasted image 20230223144623.png]]

AutoIt can be used to automate tasks in windows application and in this case the key check is done with AutoIt.
To get the script out of the .exe file I used a program called autoit-ripper: https://github.com/nazywam/AutoIt-Ripper
Once you get the script from autoit-ripper I looked for the failure string "Wrong serial! Retry" that you get from a random key input.
![[Pasted image 20230223145135.png]]
There seems to be a $KEY variable so we look for that next.
![[Pasted image 20230223145233.png]]
That lead to this part of the code. This looks like the algorithm to generate the correct key. I translate that code to python with my current username and get the correct key for the crackme.

keygen.py
```python
import os

user = os.getlogin()
userA = [ord(x) for x in user]
l = len(user)
keyA = []
for i in range(l):
    temp = userA[i] - l
    if temp == 95:
        temp += 7

    keyA.append(temp)

key = "".join([chr(x) for x in keyA])
print(key)
```

#autoit #c/cpp #completed 
