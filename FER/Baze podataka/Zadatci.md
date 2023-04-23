Za svakog korisnika ispište ime, prezime i broj profila koje ta osoba ima ako ime te osobe kreće slovom 'A' i žena je.
Rezultate sortirajte prema prezimenu silazno

----

Za svaki film koji je zaradio preko 100,000,000 dolara, ima ocjenu veću od 80 i  barem jedan korisnik je označio sa sviđa mi se, ispišite naslov filma, ocjenu i broj korisnika kojima se film svidio. 

----

Za svaki film koji je izvorno na španjolskom jeziku ispišite naslov filma. Dodatno za svaki film na španjolskom ako njegov prethodnik ima prijevod (titlove) na engleskom jeziku ispišite i naslov prethodnika inače ispišite NULL.
Rezultate poredajte po naslovu prethodnika.



SELECT firstname, lastname, COUNT(profilename)
FROM owner NATURAL JOIN profile
WHERE owner.gender = 'F' AND owner.firstname LIKE 'A%'
GROUP BY ownerid
ORDER BY lastname DESC;































### Moja rješenja
```sql
SELECT firstname, lastname, COUNT(profilename)
FROM profile NATURAL JOIN owner
WHERE SUBSTRING(firstname, 1, 1) = 'A' AND gender = 'F'
GROUP BY firstname, lastname
ORDER BY lastname DESC
```
----
```sql
SELECT tracktitle, trackrating, (SELECT COUNT(liked) FROM profiletrack WHERE trackid = up.trackid AND liked = 1)

FROM (track NATURAL JOIN movie) as up
WHERE boxincome > 100000000 AND trackrating > 80 AND 
(SELECT COUNT(liked) FROM profiletrack WHERE trackid = up.trackid AND liked = 1) >= 1
```
----
```sql
SELECT mt1.tracktitle, mt2.tracktitle
FROM 
(movie NATURAL JOIN track NATURAL JOIN (audiolang JOIN language ON audiolangid = langid)) as mt1 LEFT JOIN 
(movie NATURAL JOIN track NATURAL JOIN (subtitle JOIN language ON subtitlelangid = langid)) as mt2
ON mt1.prevmovieid = mt2.trackid AND mt2.langname = 'English'
WHERE mt1.langname = 'Spanish' AND mt1.isNative = 1
ORDER BY mt2.tracktitle
```
