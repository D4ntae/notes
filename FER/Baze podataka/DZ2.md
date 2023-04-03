Zadatak 1
```sql
SELECT jmbag, SUM(ectsbod) as upisao_ects, COUNT(*) AS upisao_predmeta
FROM (upisanpredmet NATURAL JOIN predmet) AS upit
WHERE akgodina = 2020 AND 
(SELECT COUNT(*) from upisanpredmet NATURAL JOIN predmet WHERE akgodina = 2020 AND upit.jmbag = jmbag GROUP BY jmbag) >= 6
GROUP BY jmbag

```

Zadatak 2
```sql
SELECT
	nazorgjed,
	imenastavnik AS ime,
	prezimenastavnik AS prezime
FROM orgjed LEFT JOIN (mjesto JOIN nastavnik
ON pbr = pbrstannastavnik AND nazmjesto LIKE 'Z%')
ON orgjed.siforgjed = nastavnik.siforgjed
WHERE sifnadorgjed = 36

```

Zadatak 3
```sql
UPDATE predmetgrupa SET sifnastavnik = 
(SELECT DISTINCT sifnastavnik FROM predmetgrupa NATURAL JOIN nastavnik
WHERE imenastavnik = 'Mirko' AND prezimenastavnik = 'Kasun')
WHERE sifnastavnik = (SELECT DISTINCT sifnastavnik FROM predmetgrupa NATURAL JOIN nastavnik
WHERE imenastavnik = 'Klementina' AND prezimenastavnik = 'Lapaine');
```

Zadatak 4
```sql
SELECT
	datumispit AS datum_ocjene,
	COUNT(jmbag) AS broj_kandidata,
	ROUND(AVG(ocjena), 2) AS prosjek_ocjena
FROM ispit AS upIspit
WHERE (SELECT MIN(ocjena) FROM ispit WHERE datumispit = upIspit.datumispit GROUP BY datumispit) >= 4
GROUP BY datumispit
```

Zadatak 5
```sql
SELECT
	dvorana.ozndvorana,
	kapacitet,
	COUNT(DISTINCT sifpredmet) AS razlicitiPredmeti
FROM (dvorana LEFT JOIN predmetgrupa 
	  ON dvorana.ozndvorana = predmetgrupa.ozndvorana AND akgodina = 2019)
WHERE dvorana.ozndvorana LIKE 'A%' 
AND kapacitet <=
(SELECT MIN(kapacitet) FROM dvorana WHERE ozndvorana LIKE 'D%')
GROUP BY dvorana.ozndvorana, kapacitet
ORDER BY COUNT(DISTINCT sifpredmet) DESC, ozndvorana ASC;
```

Zadatak 6
```sql
CREATE TABLE studStip (
	ime VARCHAR(25),
    prezime VARCHAR(25),
    jmbag VARCHAR(10),
    ukEcts NUMERIC(4, 1)
);

INSERT INTO studStip
SELECT imestudent, prezimestudent, jmbag, SUM(ectsbod) AS s
FROM (student NATURAL JOIN ispit NATURAL JOIN predmet) AS up
WHERE ocjena > 1 AND (SELECT SUM(ectsbod) FROM student NATURAL JOIN ispit NATURAL JOIN predmet
WHERE ocjena > 1 AND jmbag = up.jmbag) >= 80
GROUP BY imestudent, prezimestudent, jmbag
```

Zadatak 7
```sql
UPDATE predmetgrupa SET sifnastavnik = 
(SELECT DISTINCT sifnastavnik FROM predmetgrupa NATURAL JOIN nastavnik
WHERE imenastavnik = 'Danijela' AND prezimenastavnik = 'Sajko')
WHERE sifnastavnik = (SELECT DISTINCT sifnastavnik FROM predmetgrupa NATURAL JOIN nastavnik
WHERE imenastavnik = 'Ines' AND prezimenastavnik = 'Majetić');
```

Zadatak 8
```sql
SELECT DISTINCT imestudent FROM student WHERE imestudent LIKE '%i%'AND length(imestudent) = 8 AND (EXTRACT(DOW FROM datumrod) BETWEEN 1 AND 5)
```

Zadatak 9
```sql
SELECT dvorana1.ozndvorana as oznDvorana1, dvorana1.kapacitet as kapacitet1, dvorana2.ozndvorana as oznDvorana2, dvorana2.kapacitet as kapacitet2
FROM dvorana AS dvorana1 JOIN dvorana AS dvorana2 ON dvorana1.kapacitet = dvorana2.kapacitet AND dvorana1.ozndvorana <> dvorana2.ozndvorana
```

Zadatak 10
```sql
SELECT predmet.sifpredmet, nazpredmet, ozngrupa, kapacitet
FROM predmet LEFT JOIN (predmetgrupa NATURAL JOIN grupa)
ON predmet.sifpredmet = predmetgrupa.sifpredmet AND akgodina = '2021'
WHERE mod(ectsbod, 2) = 0 AND ukbrsatitjedno < 6
```

Zadatak 11
```sql
SELECT 
	upper(predmet1.nazpredmet) as nazivPredmeta1, 
	predmet1.ukbrsatitjedno as ukBrSatiTjedno1,
    upper(predmet2.nazpredmet) as nazivPredmeta2, 
	predmet2.ukbrsatitjedno as ukBrSatiTjedno2
FROM predmet AS predmet1 JOIN predmet as predmet2 ON
	predmet1.ukbrsatitjedno <> predmet2.ukbrsatitjedno AND
    predmet1.ectsbod = predmet2.ectsbod
```