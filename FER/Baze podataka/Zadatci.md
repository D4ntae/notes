Za svakog korisnika ispište ime, prezime i broj profila koje ta osoba ima ako ime te osobe kreće slovom 'A' i žena je.
Rezultate sortirajte prema prezimenu silazno

----

Za svaki film koji je zaradio preko 100,000,000 dolara, ima ocjenu veću od 80 i  barem jedan korisnik je označio sa sviđa mi se, ispišite naslov filma, ocjenu i broj korisnika kojima se film svidio. 

----

Za svaki film koji je izvorno na španjolskom jeziku ispišite naslov filma. Dodatno za svaki film na španjolskom ako njegov 


































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

