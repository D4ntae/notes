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
Prva stvar koju sam primjetio u PEView-u je sekcija s resursima u kojoj se nalazi konfiguracijski string od prije.
![[Pasted image 20230602162830.png]]
Nadalje pogled u import tablicu file-a pokazuje da malware pristupa internetu jer importa wsock32.dll i iz njega funkcije potrebne za uspostavljanje socket konekcije. Također primjećujemo funkcije za mijenjanje registry ključeva kao što su RegSetValueExW i RegCreateKeyW.
Zaglavlja svih sekcija i import tablica su normalne što nam daje doznanja da file vjerojatno nije pakiran ili enkriptiran na neki drugi način.

Iz dosadašnje analize možemo zaključiti da se malware najvjerojatnije spaja na domenu zzxx9508.codns.com i pomoću nje dobija instrukcije što da radi s inficiranim računalom. Da bismo zaključili točno kako to radi i koje su sve mogućnosti ovog malware učitat ćemo ga u Ollydbg i IDA-u i dinamički analizirati.

## Dinamička analiza
----
IDA tehnički spada u statičku analizu, ali mislim da se sa svojim graph pogledom i referencama savršeno uklapa u rad s debuggerom.
Cilj dinamičke analize je detaljno proučavanje rada malware-a i svih njegovih mogućnosti. Kroz cijelu analizu koristi se kombinacija Ollydbg-a i IDA-e.

#### Inicijalno
Kada prvo učitamo program u Olly i IDA-u vidimo da poziva 4 funkcije. Nekim funkcijama je u IDA-i promijenjeno ime radi lakšeg razumijevanja koda.
![[Pasted image 20230602215915.png]]
![[Pasted image 20230602215936.png]]
Prva funkcija nije interesantna pa krenimo na drugu.

#### Druga funkcija
![[Pasted image 20230602221133.png]]
![[Pasted image 20230602221100.png]]
Prvo vidimo da malware isključuje DEP unutar procesa tj. dozvoljava da dijelovi memorija programa poput segmenta za resurse koji ne bi smio biti postat executable postanu executable.
Nakon toga druga setupSettings funkcija uzima CFG resurs string od prije u učitava ga u varijable procesa.
CheckMutex funkcija je standardna funkcija koja koristi mutex-e da osigura da samo jedna instanca programa bude pokrenuta u bilo kojem trenutku.

![[Pasted image 20230603101944.png]]
Nakon toga program provjerava je li lokacija od kuda je pokrenut C:\\Windows\\ALYac.exe i ako nije zna da je ovo prvi put pokretanja pa kopira sam sebe u C:\\Windows\\ALYac.exe i doda registry ključ u HKLM\\ Software\\Microsoft\\Windows\\CurrentVersion\\Run\\ kako bi ostvario perzistenciju.

![[Pasted image 20230603124326.png]]
CreateThread poziv je kako meni izgleda ostatak iz developmenta malware-a jer normalno se ne pozove, ali ako se u config stringu 0 promijeni u 1 pokrene se MessageBox koji nakon što se klikne ok briše registry ključ koji osigurava prezistenciju. 
Nakon toga slijedi funkcija koja provjerava postojanje opcionalnog DLL-a u resursima koji dodaje neke dodatne mogućnosti malware-u kao što su kontrola desktopa preko VNC protokola, keylogging, kontrola web kamere itd.
Cijeli popis je na slici ispod.
![[Pasted image 20230603124857.png]]
Tu je kraj postavljanja i malware kreće uspostavljati vezu s C2 serverom na adresi zzxx9508.codns.com od kojeg će primat daljenje komande.

#### Mogućnosti malware-a
- Od prije navedene dodatne opcije
- Zatvaranje procesa na računalu pomoću TerminateProcess WinAPI-a
- Čitanje procesa i memorije procesa na računalu pomoću  CreateToolhelp32Snapshot i Toolhelp32ReadProcessMemory WinAPI-a
- Čitanje, pokretanje, zaustavljanje servisa koji su pokrenuti
- Upravljanje registry ključevima
- Enuneracija podataka o sustavu kao što je arhitektura, dostupna memorija, podatci o procesoru itd.
- Preuzimanje datoteka s URL-ova na računalo