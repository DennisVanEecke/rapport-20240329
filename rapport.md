@import "rapport.less"

# Rapport van data exploratie voor Fiscaal register

<div class="contactinfo">

Voor vragen en opmerkingen: 
  * E-mail: [dennis.van.eecke@codifly.be](mailto:dennis.van.eecke@codifly.be)
  * Rocket Chat: `dennisve`
  * Matrix: `@dennisvaneecke:matrix.org`

</div>

Datum: 29 maart 2024
Versie: 1.0

Deze analyse staat ten dienste van het uitwerken van een technische visie voor de ontwikkeling van een nieuwe applicatie die ABB ter beschikking zou kunnen stellen aan het Vlaamse publiek. De voorgestelde applicatie heeft voorlopig de naam 'Fiscaal Register' gekregen en zou moeten een gestructureerd overzicht geven aan de burger van de fiscale besluiten die genomen werden door de lokale overheid of overheden die relevant zijn voor een specifieke gebruiker (woonplaats, type). De inhoud van deze besluiten zou door de applicatie verwerkt moeten worden zodat de belasting maatregelen overzichtelijk geformatteerd worden. Een volgende iteratie van de app zou een calculatie of simulatie element moeten kunnen bevatten en dit vereist dat de data in de fiscale besluiten gestructureerd is; wat nu nog niet het geval is. In de eerste fase moet bekeken worden hoe fiscale besluiten kunnen gevonden worden per gemeente en per type gebruiker: particulier, bedrijf en organisatie (nog niet nader bepaald). Dit kan al met de huidige dataset en word in deze publicatie besproken. De analyse moet ook helpen om nieuw beleid te formuleren die lokale besturen helpt om de datakwaliteit te verbeteren en om fiscale besluiten op termijn te (her)publiceren met de fiscale rekenregels in gestructureerde vorm.

Deze analyse is opgesteld in het Nederlands door het grote aantal Nederlandstalige conceptnamen in de RDF vocabularia (e.g. 'Bestuursorgaan', 'Besluit' en 'Bestuurseenheid'). De databron voor deze analyse is een kopie van de database van de productie omgeving van de [Lokaal Beslist](https://lokaalbeslist.vlaanderen.be/) app. Deze dataset is een aggregaat van alle besluiten data gepubliceerd door lokale besturen in Vlaanderen. De informatie inzake Bestuurseenheden (BE) en bestuursorganen is afkomstig van Organisatieportaal. Meer informatie verkrijgbaar bij de auteur op eenvoudig verzoek.

## Filteren van Fiscale besluiten

Om een effectieve applicatie te kunnen bouwen moeten de besluiten kunnen gefilterd worden op de volgende manieren:

* Per type van bestuurseenheid (i.e. gemeente) geclassificeerd met `BestuurseenheidClassificatieCode`
* Per type van bestuursorgaan (i.e. gemeenteraad) geclassificeerd met `BestuursorgaanClassificatieCode`
* Per besluit 'type'; i.e. Fiscale besluiten. In de dataset van Data Vlaanderen werden de volgende types gevonden: Contantbelasting, Kohierbelasting, Aanvullende belasting en Belastingsreglement.
* In functie van compleetheid: Besluit records die onvoldoende data bevatten kunnen niet gebruikt worden. In deze analyse controleren we op de aanwezigheid van omschrijving, besluit tekst, title, taalaanduiding en een link met een artikel.

In dit rapport zullen we niet ingaan op de verschillende filtertechnieken en hoe word gecompenseerd voor de wisselende datakwaliteit. Dit zijn de resultaten.

| # Totaal | # gelinkt aan gemeente | # Met besluit type | # Met fiscaal type | # Fiscaal & compleet | # Fiscaal & compleet & gelinkt |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 2.434.838 | 301.471 | 77.737 | 2.067 | 546 | 483 |

De queries om deze resultaten te bekomen zijn gepubliceerd op GitHub. We kunnen zien dat er slechts een héél kleine hoeveelheid besluiten gelinkt (aan gemeente en gemeenteraad) zijn én een fiscaal type (`BesluitType`) hebben én compleet zijn. Dit heeft te maken met data kwaliteit want wanneer we louter naar de besluiten kijken met het fiscale type dan komen we uit op 2k. Ergo: Ongeveer 1,5k besluiten zijn wel fiscaal maar niet compleet en niet correct gelinkt.

De volgende stap in de analyse is om te bekijken hoe deze fiscale besluiten verdeeld zijn over de gemeenten:

@import "./municipality-count-table.md"

In de lijst hierboven zijn slechts 49 gemeenten aanwezig. De overige gemeenten hebben geen fiscale besluiten of deze besluiten waren niet gelinkt/geclassificeerd/incompleet. Het totaal van alle beslissingen is 483; zoals in de eerste tabel aangegeven. 


