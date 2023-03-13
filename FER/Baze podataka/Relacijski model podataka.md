
### Pojmovnik
- Relacija - imenovana 2D tablica, tj skup svih opisa entiteta
- Atribut - imenovani stupac relacije
- Domena - skup dopuštenih vrijednosti atributa
- n-torka - redak relacije, skup parova oblika *atribut : vrijednost atributa*
- Relacijska shema = RELACIJA + atributi (MJESTO = {pbr, naziv, sifZup})
- Stupanj relacije - broj atributa(stupaca)
- kardinalnost relacije - broj redaka

###### A-vrijednost n-torke
- t(A) predstavja vrijednost koju atribut A poprima u n-torki
- t = {matbr: 102, prez: Novak}
- t(prez) = Novak

###### X-vrijednost n-torke
- t(X) označava n-torku t reduciranu na skup atributa X

### SQL - Structured Query Language

- temeljen na relacijskom modelu podataka
- jedan SUBP može istovremeno upravljati s više baza podataka
- JEDNAKO JE =,  A NIJE JEDNAKO JE <>!

>[!tip] Creation & Destruction
> CREATE DATABASE *ime*;
> DROP DATABASE *ime*;

>[!tip] Upisivanje & Dohvat
> INSERT INTO *ime* VALUES (X, Y, Z);
> SELECT * FROM *ime* WHERE atr = a;

>[!tip] Izmjena vrijednosti & brisanje
> UPDATE *ime* SET atr1 = X WHERE atr2 = Y;
> DELETE FROM *ime* WHERE atr = X;


### Relacijska algebra



- operacije se specificiraju navođenjem predikata : r = {t | F(t)}
- rezultat je skup n-torki t za koje je vrijednost predikata F istina
>[!tip] UNIJA (OR)
> - UNIJSKA KOMPATIBILNOST - pri korištenju operacije unije moramo se pobrinuti da su relacije unijski kompatibilne tj da su to relacije istog stupnja(broj stupaca) te da su korespondentni atributi definirani nad istim domenama (integeri, charovi...)
> SELECT * FROM *ime*
> 	 UNION
> SELECT * FROM *ime2*

>[!tip] UNION ALL - MULTISKUP 
> - rezultat nije relacija nego set svih n-torki koji pripadaju navedenim relacijama
> SELECT * FROM *ime1* 
> 	UNION ALL
> SELECT * FROM *ime2*

>[!tip] PRESJEK (AND)
>SELECT * FROM *ime1*
>	INTERSECT
>SELECT * FROM *ime2*

>[!tip] RAZLIKA
> - rezultat je relacija čije su n-torke elementi r1, a nisu elementi r2 
> SELECT * FROM *ime*1
> 	EXCEPT
> SELECT * FROM *ime2*

>[!tip] SELEKCIJA
> - rezultat su n-torke za koje je vrijednost predikata TRUE
> SELECT SELECTList FROM *ime*
> - SELECTList određuje koji će se atributi pojaviti u rezultatu 

>[!tip] PROJEKCIJA (pi)
> - najjednostavnije rečeno, eliminira *stupce*
> - mijenja se stupanj relacije (iako u originalnoj relaciji nema duplikata moguće je da u novonastaloj ima pa se kardinalitet može promijeniti)
> - u listi za selekciju navode se oni atributi koje želimo zadržati iz tablice relacije
> - SELECT nazMjesto, pbr FROM mjesto;
> - tablica je *relacija* akko ima ime, zato rezultat projekcije *nije* relacija
> - SQL neće po definiciji napraviti relaciju iz našeg upita tj neće izbaciti duplikate pa <mark style="color: #FFB8EBA6; background: transparent">trebamo u naredbu dodati ključnu riječ DISTINCT nakon SELECT</mark>
>

>[!tip] KARTEZIJEV PRODUKT (SVAKI SA SVAKIM)
> - imamo relacije r i s pri čemu im je presjek prazan skup, obavljanjem operacije rxs dobiva se relacija p = r unija s tj r+s
> - deg(p) = deg(r) + deg(s)
> - card(p) = deg(r) * deg(s)
> - n-torke se dobivaju tako da se svaka n-torka iz rsparuje sa svakom n-torkom iz s
> - SELECT * FROM *tablica1, tablica2*;
> PROBLEM : što ako presjek r i s nije prazan skup?
> npr i r i s tablica imaju naziv stupca B -> TO NIJE RELACIJA, ne smiju imati isti naziv stupaca pa moramo prvo provesti operaciju PREIMENOVANJA
> možemo preimenovati samo relaciju ili relaciju i atribute
> svaki put kada preimenujemo atribute "gazimo" SVE atribute tj ako želimo preimenovati samo 3.stupac moramo za sve stupce zapisati njihova stara imena i promijeniti 3.
> - preimenovanje atributa: SELECT <mark style="color: #FFB8EBA6; background: transparent">sifZup AS sifraZ</mark> FROM tablica
> - obzirom da ako radimo preimenovanje atributa oni imaju isto ime moramo SQL-u pojasniti atribut KOJE relacije želimo preimenovati pa to radimo dot notacijom tj primjerice r.B (stupac B iz relacije r)

>[!tip] PRIRODNO SPAJANJE
> - r ima atribute a, b i c, a relacija s c, d i e pa je rez relacija p = a,  b, c, d, e
> - svaka n-torka se pokušava spojiti sa svakom, a spajaju se samo ako imaju istu  vrijednost nekog atributa
> - napravimo Kartezijev produkt pa filtriramo
> - SELECT mjesto.*, zupanija.nazZup FROM mjesto NATURAL JOIN zupanija
> - to znači: odaberi sve atribute iz relacije mjesto i atribut nazZup iz relacije zupanije i napravi nad njima kartezijev produkt pa filtriraj 
> - stavili smo ovaj zupanija.nazZup da nam nebi doslo do ponavljanja stupaca pa moramo rucno odvojit to da nam se ne sjebe i kaze da to nije relacija!!
> - Najčešća sintaksa: SELECT mjesto.*, zupanija.nazZup FROM mjesto NATURAL JOIN zupanija (on po defaultu onda gleda koji su atributi dupli)

>[!tip] SPAJANJE UZ UVIJET (THETA - SPAJANJE) 
> - rezultat je relacija koja sadrži n-torke iz operacije Kartezijevog produkta za koje je predikat tj uvjet F = TRUE
> - SELECT * FROM linija JOIN zrakoplov ON uvjet

>[!tip] SPAJANJE S IZJEDNAČAVANJEM (Equi-join)
> - basically radi isto kao prirodno spajanje ali primitivnije - napravi kartezijev produkt dvije relacije i onda mu u uvjetu kažemo zadrži samo one n-torke gdje su vrijednosti dva atributa koja mu damo u uvjetu jednaka
> - SELECT * FROM mjesto, zupanija WHERE sifZup = sifraZupanije



>[!tip] AGREGACIJA
> - uzme stupac, primijeni na njemu neku agregatnu funkciju, rezultat je relacija stupnja 1 i kardinalnosti 1 (spoljšti stupac)
> - Agregatne funkcije - COUNT, SUM, AVG, MIN, MAX
> - sufiks -DISTINCT na ove funkcije znači da će zanemariti eventualne duplikate
> - moramo paziti da je rezultat neimenovana relacija pa samim time i *nije* relacija pa nakon primjene agregatnih funkcija ju moramo preimenovati tj dati joj ima da ona postane relacija
> - SELECT AVG(ocjena) AS prosjOcj FROM ispit;
> - moguće je odjednom izračunati više agregatnih vrijednosti unutar jedne naredbe pa ćemo dobiti relaciju dimenzija 1 x broj agr operacija
> - SELECT COUNT(stupacX) AS broj1, MIN(stupacY) AS broj2 FROM osoba;
> - ako hoćemo npr iz tablice svih visina ljudi u nekom razredu vidjeti koliko ima različitih visina ljudi onda koristimo DISTINCT odnosno ovako:
> - SELECT COUNT(DISTINCT visina) AS broj1 FROM osoba;

>[!tip] AGREGACIJA I GRUPIRANJE
> - npr želimo izračunati prosjek predmeta matematika i fizika tj ne prosjek svega nego prosjek svih ocjena *po predmetu*
> - rezultat želimo da bude u formatu da su stupci jedinstveni predmeti, a drugi stupac njihovi prosjeci
> - Grupiranje - prvo radimo "podtablice" pa onda njih sabijamo i računamo
> - isto moramo obaviti preimenovanje stupaca da bi dobili relaciju
> - SELECT *one atribute koje želim u rezultatu* FROM *iz koje tablice* GROUP BY *atributi po kojima grupiram*
> - kada pišemo select listu a imamo sql upit sa grupiranjem u Select listu smijemo staviti samo grupirajuće atribute ili ako oni nisu grupirajući moraju biti pod agregatnom funkcijom!





















