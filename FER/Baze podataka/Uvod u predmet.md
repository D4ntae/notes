- Informacijski sustav - Ukupna infrastruktura, organizacija, osoblje i komponente koje služe za prikupljanje, obradu, pohranu, prijenos, prikaz, širenje i raspolaganje informacijama
- središnji dio info sustava je BAZA PODATAKA

### Pojmovi 

- Entitet - bilo što, što ima suštinu ili bit i posjeduje značajke s pomoću  
kojih se može razlučiti od svoje okoline, posjeduje *atribute tj svojstva* koja ga karakteriziraju
- Skup entiteta - slični entiteti - slični su ako im se promatraju ista svojstva, npr. Predmet, Zaposlenik...
- basically entiteti na primjeru predmeta su matematika, fizika, a na razini skupa entiteta su predmet
- Domena -  vrijednost atributa odabrana iz nekog skupa vrijednosti, npr. domena atributa bodoviNaIspitu je vrijednost iz skupa prirodnih brojeva 1-5
- Identifikatori / ključevi skupa entiteta - skupovi atributa čije vrijednosti jednoznačno određuju entitet, tj u tablici gledamo dali su u stupcu pojedinog atributa sve vrijednosti *različite*

## Model podataka

- formalni sustav koji koristimo kod modeliranja baze podataka
1. Relacijski model - objekti su ovdje *relacije* - skupovi n-torki (retci tablice koji pridaju po jednu vrijednost svakog atributa jednom entitetu)
- shema relacije = naziv relacijske sheme + skup atributa
- Operacije : selekcija (sigma), unija, razlika, presjek, projekcija...
2. ER model podataka - objekti su entiteti i njihove međusobne veze

### Arhitektura baze podataka

- Konceptualna (logička) shema - opis svih entiteta i veza, atributa, domena i integritetska ograničenja
- Interna shema - kako su podaci pohranjeni i koje se metode koriste za pristup podacima - *izmjena interne sheme ne utječe na konceptualnu shemu*
- Eksterna shema - pogleda na dio baze podataka namijenjen specifičnoj grupi korisnika

### Sustav za upravljanje bazom podataka (SUBP)

- programski sustav koji omogućava upravljanje podacima u bazi podataka
##### Jezici baze podataka
1. DDL (data definition language) - imenovanje i opis entiteta, atrbuta, veza, i pripadnih ograničenja integriteta i pravila sigurnosti
- koristi se za **definiranje nove sheme baze podataka / modificiranje postojeće**
2. DML (data manipulation language) - omogućava korištenje skupa operacija za rukovanje podacima u bazi podataka, **query language**

