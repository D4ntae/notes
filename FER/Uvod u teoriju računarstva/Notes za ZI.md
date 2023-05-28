Rekurzivno prebrojivi jezici - TS ne mora dati odgovor za nizove koji nisu u jeziku
Rekurzivni jezici - TS daje odgovor i za nizove koji nisu u jeziku

Jezik L jest rekurzivno prebrojiv ako i samo ako postoji TS M1 koji generira jezik G(M1) = L

Za bilo koji TS M1 koji generira jezik G1 moguće je izgraditi TS M2 koji prihvaća jezik G1

Za bilo koji TS M2 koji prihvaća jezik L1 moguće je izgraditi TS M1 koji generira jezik L1

Rekurzivne jezike moguće je generirati kanonskim slijedom. Kanonski slijed znači da idu nizovi od kraćeg prema dužem. Npr. e, 0, 1, 00, 01, 10, 11, 000, ...

Jezik koji je moguće generirati kanonskim slijedom jest rekurzivni jezik

Gramatika neograničenih produkcija je gramatika oblika alfa -> beta

Ako gramatika neograničenih produkcija generira jezik L onda jezik L jest rekurzivno prebrojiv jezik.

Ako TS M prihvaća rek. preb. jezik L onda postoji gramatika G neograničenih produkcija koja generira jezik L.

Unija dvaju rekurzivnih jezika jest rekurzivni jezik

Unija dva rekurzivno prebrojiva jezika jest rekurzivno prebrojiv jezik

Komplement rekurzivnog jezika jest rekurzivni jezik

Univerzalni jezik Lu jest rekurzivno prebrojiv, odnosno izračunljiv

Univerzalni jezik Lu nije rekurzivan, odnosno nije odlučiv

Dijagonalan jezik nije niti izračunljiv niti odlučiv tj. viša razina je čak i od rekurzivno prebrojivih jezika

Kontekstno ovisni jezici su zatvorni s obzirom na sve operacije

Komplement determinističkog kontekstno ovisnog jezika jest deterministički  
kontekstno ovisni jezik

Kontekstno ovisni jezici su pravi podskup rekurzivnih jezika

![[Pasted image 20230528192330.png]]

![[Pasted image 20230528192403.png]]

Ako TS MI s k radnih traka prostome složenosti S(n) prihvaća jezik L(M1), onda postoj i TS M2 s jednom radnom trakom koji je jednake prostome složenosti S(n) i koji prihvaća jezik L(M2)=L(M1)

Ako TS MI s k traka vremenske složenosti T(n) prihvaća jezik L(M ), onda postoj i TS M2 s jednom trakom koji je vremenske složenosti T^2(n) i koji prihvaća jezik L(M2)=L(MI)

Ako je jezik L u klasi DTIME(j(n)), onda je jezik L u klasi  
DSPACE(j(n))

Ako je jezik L u klasi DSPACE(f(n)) i ako za funkciju f(n) vrijedi f(n) >= log2n onda je jezik L u klasi DTIME(c^f(n)). Vrijednost konstante c ovisi o jeziku L

Ako je jezik L u klasi NSPACE(f(n)) i ako je funkcija f(n) >= log2n potpuno prostorno izgradiva onda je jezik L u klasi DSPACE(f^2(n))