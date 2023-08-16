# Barometer logik

[Demo her](https://boligskat-barometer-git-textbtm-adviceas.vercel.app/)

Jeg, Mathias, kan kontaktes på <br>
mahtias.j@forteadvice.com <br>
53 64 02 70

## json data

Det tilsendte json-data er et array med objekter for alle 98 kommuner i DK. <br>

```JSON
[
  {
    kommune: "string",
    hus: { // EjendomstypeObject
      billigere: {
        resultat: Number,
        text: "string" // ex "1.2 mio" - så valgmuligheden "Under 1.2 mio"
      },
      typisk: {
        resultat: Number,
        text: "string"
      },
      dyrere: {
        resultat: Number,
        text: "string"
      },
    },
    ejerlejlighed: EjendomstypeObject,
    sommerhus: EjendomstypeObject,
  },
]
```

Hvert kommune-objekt har som minimum have 1 af ejendomstyperne (hus, ejerlejlighed, sommerhus) <br>

Hvis en ejendomstype ikke findes for den pågældende kommune, skyldes dette at der ikke er nok data for ejendomstypen, til at lave beregninger. <br>

Dette skal selvfølgelig håndteres med en fejlbesked - prøv evt sommerhuse for 2100 københavn i demoen. <br>

Hver ejendomstype (hus, ejerlijlighed, sommerhus) er inddelt i "billigere", "typisk" og "dyrere", hvilke bliver omsat til "under", "mellem" og "over" i fronten. <br>

"text" er den beregenede værdi som skal bruges i fronten <br>

"resultat" er ... resultatet <br>
1: sandsynlighed for skattelettelse <br>
2: sandsynlighed for skattestigning <br>
0: sandsynlighed for uændret skat<br>

Derfor er "vurdering", "skattelettelse" og "skatterabat" overflødige - og bliver nok fjernet.

<br>

## DAWA postnummer API

Vi har brugt DAWA til at slå postnumre op. <br>
Da få postnumre kan overlappe flere kommuner, skal det i disse tilfælde være muligt at kunne vælge den specifikke komme. <br>

Prøv evt postnummeret 2791 i demoen

<br>
