Kada pokrenemo program vidimo da traži username i password. Ako upišemo neke testne podatke vidimo da program ispisuje "Wrong!". Otvorimo program u Olly-u i tražimo string "Wrong!". Kada otvorimo sve stringove koje Olly može naći primjećujemo i string "Correct!". Ako pogledamo odmah prije "je" instrukcije koja vodi u krivi put je instrukcija koja provjerava je li registar "eax" postavljen na 0. Iznad te instrukcije zamijećujemo call na neki dio koda i zaključujemo da taj dio koda postavlja "eax" na 0 ako password nije dobar pa je taj dio koda funkcija koja provjerava točnost lozinke. Pseudo kod te funkcije je ispod.

```pseudocode

bool check(username, password) {
	if ( len(username) > 16 or len(username) < 6 ) return 0; // username mora biti između 6 i 16 znakova

	sum = 0;
	for (i = 0; i < len(username); i++) {
		temp = 0;
		temp = username[i] * 0x460b; // ascii kod znaka
		temp = temp << (i & 7);
		sum += temp;
	}

	if (sum == password) return 1;
	else return 0;
}

```

Moj jmbag: 0036541606
Password: 241996776