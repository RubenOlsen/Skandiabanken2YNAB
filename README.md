Skandiabanken2YNAB
==================

2022-02-15: Det finnes nå bedre måter å gjøre dette på i 2022 så dermed arkiverer jeg dette repoet.

Noen repoer å sjekke ut er f.eks.: 

* https://github.com/stenjo/SbankenToYNAB
* https://github.com/elzapp/sbanken-ynab
* https://github.com/Wedvich/sbanken-ynab
* https://github.com/danmusk/sbankenYNAB
* https://github.com/torryt/sbanken-ynab-importer
* https://github.com/andrefau/Sbanken-YNAB

Det er også andre repos på GH som gjør denne jobben - listen over er ment som eksempler.

Jeg vil ikke gi råd om hvilken av disse du bør bruke.

----------------------------------------------------------------

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

Eksport fra Skandiabanken er å benytte tabulator som kolonneskilletegn og desimal-punktum som øreskilletegn.

For kategorien _Varekjøp_ så stripper scriptet bort de 5 første tegnene i _tekst_-kolonnen og benytter resten som verdi for YNAB _Payee_ kolonnen. Dette ser ikke nødvendigvis så veldig pent ut når man tar ut rapporter - men det er ganske generisk og krever ikke mengder av spesialhåndteringer.

## Kategorifil
Kategorifilen inneholder en enkel hash-tabell hvor nøkkel er regexp-streng man ønsker å matche mot _tekst_-kolonnen i fra Skandiabanken sin kontoutskrift og tilhørende YNAB _Category_. Observer at YNAB sine supportsider for CSV-import foreskriver at kategorier må eksistere ved import. Se [http://www.youneedabudget.com/support/article/csv-file-importing]() for mer informasjon.

## Begrensninger
* Scriptet tar ikke og håndterer typene _Overføring_ eller _Minibank_. Når scripet treffer på disse linjene i kontoutskriften blir disse skrevet ut til skjermen og du må håndtere disse manuelt.
* Scriptet har ikke støtte for kontoutskrifter fra Skandiabanken kredittkort.
* Scriptet virker for vår husholding på våre datamaskiner - det er ingen garanti at dette vil virke på din datamaskin ;-)

## Lisens
Lisensen for dette scriptet er veldig enkel: 

* Gjør Hva Du Vil, men ikke ikke forvent at scripet virker eller ikke ødelegger dataene dine. 
* Du kan heller ikke påstå at du har skrevet dette selv, det har Ruben Olsen Lærk gjort.
* All bruk av scriptet skjer på egen regning og risiko. Ruben Olsen Lærk har intet ansvar for bruk - herunder support.

## Forking
Du er hjertelig velkommen til å forke fra GitHub [https://github.com/RubenOlsen/Skandiabanken2YNAB]() og be om pull-request dersom du har nyttige forbedringer eller feilfikser.

