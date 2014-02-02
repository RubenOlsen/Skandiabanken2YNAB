Skandiabanken2YNAB
==================

Dette er et enkelt script som konverterer CSV eksport fra Skandiabanken til CSV formatet som You Need A Budget krever.

Grunnen til at det ligger ute på GitHub er:

* Jeg er for kjip til å betale for et privat repo kun for dette scriptet.
* Andre folk kan ha nytte av dette.

Observer at dette er et suprtraskt og skitent hack for å løse en enkelt ting: Importere data til YNAB for husholdningen. Scriptet krever en del håndholding for å fungere optimalt for den enkelte bruker. Mao scriptet er ikke veldig robust.

I husholdningen så har vi både felleskonti og private konti. Vi er ikke mer strukturert enn at vi betaler inn på fellesting både fra privatkonti og fra felleskonti. Vi har kun definert ett budsjett.

## Bruk
Skriptet fungerer slik at det tar utgangspunkt i innhold fra tekstkolonnen i kontoutskriften til Skandiabanken og førsøker å regexp matche dette til informasjon i en hashtabell for å kunne plukke ut korrekt YNAB Category.

Det følger med en testkontoutskrift med tilhørende testkategorier - disse kan du bruke for å komme raskt i gang.

For å kjøre en konvertering gjør du som følger

`skan2ynab kontoeksportfil.csv YNAB-kategorifil`

Eksempel med medfølgende testdata:

`skan2ynab testkontodata.csv testkategorier`

Resultatfilen prefixes med _YNAB-_ og navnet på inputfilen. I eksempelet over vil resultatfilen bli hetende _YNAB-testkontodata.csv_.

Eksport fra Skandiabanken er å benytte tabulator som feltskille og desimal-punktum som øreskilletegn.

## Kategorifil
Kategorifilen inneholder en enkel hash-tabell hvor nøkkel er regexp-streng man ønsker å matche mot _tekst_-kolonnen i fra Skandiabanken sin kontoutskrift og tilhørende YNAB _Category_. Observer at YNAB sine supportsider for CSV-import foreskriver at kategorier må eksistere ved import. Se [http://www.youneedabudget.com/support/article/csv-file-importing]() for mer informasjon.

## Begrensninger
* Scriptet tar ikke og håndterer typene _Overføring_ eller _Minibank_. Når scripet treffer på disse linjene i kontoutskriften blir disse skrevet ut til skjermen og du må håndtere disse manuelt.
* Scriptet har ikke støtte for kontoutskrifter fra Skandiabanken kredittkort.

## Lisens
Lisensen for dette scriptet er veldig enkel: 

* Gjør Hva Du Vil, men ikke ikke forvent at scripet virker eller ikke ødelegger dataene dine. 
* Du kan heller ikke påstå at du har skrevet dette selv, det har Ruben Olsen Lærk gjort.
* All bruk av scriptet skjer på egen regning og risiko. Ruben Olsen Lærk har intet ansvar for bruk - herunder support.

## Forking
Du er hjertelig velkommen til å forke fra GitHub [https://github.com/RubenOlsen/Skandiabanken2YNAB]() og be om pull-request dersom du har nyttige forbedringer eller feilfikser.

