Writeup vezan za 3. domaću zadaću u sklopu predmeta REVENGE na FER-u.
Autor: Danko Delimar, 0036541606
File-hash: 60073c76350d02a89fe4e57cf7b73c6f107058be

## Statička analiza
----
#### Virus Total
Prije ikavih akcija na virtualnoj mašini pokrenuo sam hash datoteke kroz VirtusTotal da vidim je li ovo već od prije poznat malware.
![[Pasted image 20230602152939.png]]
Iz VirusTotal-a može se vidjeti da je ovo već od prije dobro poznat malware i da ga je prepoznat kao Trojan/Backdoor/Spyware, a kasnija će analiza pokazati zašto.

Nakon VirusTotal-a sljedeća dva koraka bila su mi izvlačenje stringova i otvaranje file-a u PEView-u.

#### Strings
Link na sve stringove: https://pastebin.com/PAKT2mz2
U stringovima vidimo nekoliko interesantnih stringova:
- MUTEX_BOZOK - ime mutex-a po kojem je ovaj malware i dobio ime
- Software\\Microsoft\\Windows\\CurrentVersion\\Run\\ - indikacija da malware koristi registry keyeve za perzistenciju
- TestServer|gCIUbXcNYv6tk|ALYac.exe|ALYac|ext.dat|1234|1|1|0|1|1|1515|zzxx9508.codns.com*|1|  - izgleda kao config string, analizirano poslije

#### PEView
Prva stvar koji