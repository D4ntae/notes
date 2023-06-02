RAT

Sample pristupa internetu jer u importima koristi funkcije za pristup internetu
![[Pasted image 20230530150224.png]]

PEiD output
![[Pasted image 20230530150349.png]]

SIGNATURES:
	MUTEX_BOZOK, prjBozok.exe, mypass

File koprira sam sebe u ALYac.exe izvršava c:\\Windows\\ALYac.exe i provjerava jel se executa od tam, ako ne fail

File detektira postojanje debuggera pomoću OutputDebugStringA koja mijenja zadnji error ako postoji debugger

File se upisuje u regkey LocalMachine\\Software\\Microsoft\\Windows\\CurrrentVersion\\Run

Potencijalni server: zzxx9508.codns.com

File ima cmd ili visual mode