jjj- ponekad se dešava da informacije koje treba unijeti u bazu podataka:
1. trenutno nisu poznate (neispunjeno u tablici)
2. nisu primjenjive (npr zanimanje osobe rođene 2019.)
3. do njih nije moguće doći (npr broj računa neke osobe)

- NULL vrijednost se interno pohranjuje drugačije od bilo koje druge dopuštene vrijednosti (nije 0, nije 0.0 itd)
- NULL vrijednost je neovisna od tipa podatka kojeg predstavlja
- ako npr imamo stupac placa i hocemo ispisat place u dolarima, u naredbi di dijelimo preimenujemo ga u neki smisleni naziv npr AS placaUDolarima

#### Operacije s NULL
- NULL - NULL = NULL
- NULL + 5 = NULL
- 0 * NULL = NULL
- Usporedba s NULL: -5 < NULL? (unknown)
									- NULL = NULL (unknown)
- u selekciji ako je vrijednost predikata F false ILI UNKNOWN ta n-torka se neće prikazati u rezultatu
- ako želimo dobiti te n-torke gdje je neka vrijednost onda je sintaksa "WHERE vrijednost IS NULL" ili "WHERE vrijednost IS NOT NULL"

>[!tip] AND
> true + unknown = unknown
> false + unknown = false

>[!tip] OR
> true + unknown = true
> false + unknown = unknown

>[!tip] NOT
>unknown NOT unknown = unknown

#### NULL vrijednosti i skupovi
- dopuštena je pojava *samo jedne* NULL vrijednosti u skupu
- Kopija n-torke - korespondentni atributi moraju biti ili jednaki ili oboje NULL
- Kod **projekcije** s NULL-vrijednostima u principu ne pazimo na niš, vrijedi sve kao inače -> prvo izdvojimo stupce koje hoćemo (međurezultat) i onda iz njih mičemo duplikate
- kod **Kartezijevog produkta** NULL vrijednosti nikako ne utječu!
- kod **spajanja uz uvjet i spajanja s izjednačavanjem** moramo voditi računa da se spajaju samo one n-torke koje spajanjem ne sadržavaju NULL vrijednosti
- kod **Agregacije** -> 2 slučaja: ako su sve vrijednosti za koje se izračunava agregatna funkcije NULL vrijednosti ili ako se agregatna funkcija izračunava za prazan skup rezultat funkcije COUNT = 0, a ostalih funkcija NULL
- 2.slučaj - ako među vrijednostima za koje se računa agrf ima vrijednosti koje nisu NULL onda se one u računu zanemaruju
- ako hoćemo izbrojati sve n-torke neke relacije onda imamo funkciju COUNT(zvjezdica)
- kod **grupiranja** - sve isto kao normalno samo uzimamo u obzir da je i NULL - NULL grupa

>[!tip] Lijevo vanjsko spajanje
> - sve n-torke neke relacije će se pojaviti u rezultatu spajanja 
> - n-torkama "lijeve" relacije za koje ne postoje odgovarajuće n-torke u "desnoj" relaciji se kao vrijednost atributa iz "desne" relacije postavljaju NULL vrijednosti
> - SELECT mjesto.+, zupanija.+ FROM mjesto LEFT OUTER JOIN zupanija ON sifzup=sifrazup
> - tablica tocka zvjezdica znaci uzmi sve iz te tablice (ili samo zvjezdica)
- IDENTICNO VRIJEDI ZA DESNO SPAJANJE
- SVE n-torke će se pojaviti u rezultatu spajanja ako se primijeni operacija PUNOG VANJSKOG SPAJANJA