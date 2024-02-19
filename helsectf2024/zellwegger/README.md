CTF: Helsectf
Kategori: Stego

------------------ Oppgavetekst ----------------------

Jeg brukte DALL-E til å generere et bilde med følgende beskrivelse:

ones and zeros as electrical pulses over a set of power lines

Jeg syntes det var en passende beskrivelse siden jeg har skjult et tier-bit enkodet flagg i bildet.

Husk! Det er viktig å ha en god start puls i hvert ledd av den minst betydninsgfulle biten i diagrammet.

------------------------------------------------------

Fra oppgaven får vi en png fil som heter zellweger.png

basert på oppgaveteksten er det gjemt data i de minst signifikante bitene i bildets piksler

Et kjapt googlesøk ledet meg til githubsiden til et python skript, pylsb, som henter data fra disse bitene og konstruerer tekst fra dem 

https://github.com/RenanTKN/pylsb

Jeg brukte dette skriptet med kommandoen:

```
python3 pylsb.py -i zellweger.png -r

```

Og fikk følgende data som output:

```
v@è8°©ÀY'À;³Å
t\l N3`
ä:èèÈ▒8
       ¬6
+®@è
ä°ºrfÑNè:È´ÀU`Z`ªÀCàaHR0cHM6Ly9kZS53aWtpcGVkaWEub3JnL3dpa2kvRGVjYWJpdA==
```

Jeg gjenkjente sluttdelen av dataen som base64 encoded tekst

Når teksten ble decoded fikk jeg en wikipediaside:

https://de.wikipedia.org/wiki/Decabit

Dette gir mening med oppgaveteksten, som hinter til powerlines og elektriske pulser.

En decabit er et ti-sifret signal med fem høye og fem lave signaler. For eksempel: ++--+-+--+

Dette betyr at vi må finne mer data, også bruke en decabit decoder for å finne klarteksten. Jeg så deretter på resten av dataen fra pylsb skriptet.

Med hjelp av chatgpt fikk jeg omgjort pylsb skriptet til å heller skrive ut den binære dataen istedenfor ascii

Resultatet av dette var en rekke ti-sifrede binære verdier med svært mange nuller mellom seg. Med et til python script fikk jeg fjernet null-paddingen og skrevet ledende 1-er og de etterfølgende 9 sifrene til en egen tekstfil. Jeg gjorde så de binære verdiene om til decabit (0 -> - og 1 -> +) og forsøkte å bruke dcode.fr sin decabit decoder
https://www.dcode.fr/decabit-code

Jeg fikk dårlig resultat, og innså at alle decabitene hadde 6 +'er og 4 -'er. Derfor redigerte jeg python skriptet til å ikke inkludere ledende 1-er, men heller de etterfølgende 10 sifrene

Det ga 5 +'er og 5 -'er i hver decabit, noe som er et krav for signalene

Ved bruk av dcode.fr fikk jeg dermed flagget

```
helsectf{bilde_steg0_done_r1ght__no_pun_intend3d_:):)}
```
