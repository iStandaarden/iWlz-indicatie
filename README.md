# iWlz-Indicatieregister 2
**iWlz-Indicatieregister bevat de [Graphql-schema](/gql-specificatie) koppelvlak specificatie en voorgeschreven [GraphQL-query templates](/gql-query/) voor het raadplegen van Wlz Indicatiegegevens in het indicatieregister en de [notificaties](/notificaties) verzonden vanuit het indicatieregister.**

Het indicatieregister is in beheer bij het CIZ en is onderdeel van het iWlz-netwerkmodel.

## Versies en Status 

Er zijn altijd minimaal twee versies actueel. Een versie die in productie is, status is *Lopend* en een versie die in ontwikkeling is, status is *In ontwikkeling*.

| | LOPEND (*default branch*) | IN ONTWIKKELING | ARCHIEF |
| --: |:-- |:-- | :-- |
| ***Informatiemodel***| [**Indicatieregister 2**](https://informatiemodel.istandaarden.nl/informatiemodel/iwlz/netwerk/indicatieregister-2/) (*huidige branch*) | -- | [Indicatieregister 1](https://informatiemodel.istandaarden.nl/iWlz-Indicatie-1/) |
| ***Koppelvlak specificatie*** | [Documentatie](https://github.com/iStandaarden/iWlz-indicatie/tree/Indicatieregister-2) / [Release v1.6.5] | -- |  [Documentatie](https://github.com/iStandaarden/iWlz-indicatie/tree/Indicatieregister-1) / [Release v1.2](https://github.com/iStandaarden/iWlz-indicatie/releases/tag/v1.2) |
| ***Datum*** | 27-11-2025 - [Changelog](/CHANGELOG.md)| -- | juli 2023 |

### Changelog
Volledige Changelog [Hier](/CHANGELOG.md)

## Inhoudsopgave
- [iWlz-Indicatieregister 2](#iwlz-indicatieregister-2)
  - [Versies en Status](#versies-en-status)
    - [Changelog](#changelog)
  - [Inhoudsopgave](#inhoudsopgave)
  - [Onderdelen](#onderdelen)
    - [Graphql-schema](#graphql-schema)
    - [Graphql-query](#graphql-query)
    - [Open Agent Policy](#open-agent-policy)
    - [Notificaties](#notificaties)
  - [**Raadplegen Indicatieregister**](#raadplegen-indicatieregister)
    - [Autorisatieregels en autorisatiematrix](#autorisatieregels-en-autorisatiematrix)
  - [Aanvullende Documentatie](#aanvullende-documentatie)
    - [Informatiemodel](#informatiemodel)
    - [GraphQL](#graphql)
    - [Open Agent Policy](#open-agent-policy-1)
  - [Meer informatie](#meer-informatie)
  - [Contactpersonen:](#contactpersonen)

## Onderdelen
De koppelvlak specificatie van het Indicatieregister maakt onderdeel uit van de **iStandaard iWlz**. De specificaties van de andere onderdelen, zoals ERD, regels, procesbeschrijving, autorisatieregels, notificatie-typen staan in het [Informatiemodel iWlz](https://informatiemodel.istandaarden.nl/) dat te vinden is via de website: [https://informatiemodel.istandaarden.nl/](https://informatiemodel.istandaarden.nl/)

![onderdelen](/src/Onderdelen_Netwerk.png)
v.l.n.r. Raadpleger doet via GraphQL-query een raadpleging. Open Policy agent controleert of query voldoet aan autorisatie-regels van dat register. GraphQL-schema definieert het data-schema van het register.

### Graphql-schema 
De [Graphql-schema specificatie](/gql-specificatie/) is bedoelt voor implementatie door de bronhouder en beschrijft hoe de data aan elkaar is gerelateerd. 

> [!NOTE]
> De graphql-specificatie is te vinden in de folder [**/gql-specificatie**](/gql-specificatie/). 

### Graphql-query
De [Graphql-queries](/gql-query/) beschrijven het template hoe een raadpleger vanuit zijn rol informatie kan raadplegen. Deze template volgt altijd het GraphQL-schema maar moet op bepaalde momenten aan vaste patronen voldoen vanwege de geldende autorisatie. Gaat een raadpleger buiten dit patroon dan zal de vraag worden afgekeurd en krijgt de raadpleger geen inzicht in de data. 

> [!NOTE]
> Het overzicht van de beschikbare templates inclusief een toelichting voor welke partij de template is en autorisatieflow is te vinden in de folder [**/gql-query**](/gql-query/) staat .

### Open Agent Policy
De Open Agent Policy controleert of een query voldoet aan de daarvoor afgesproken template. De policy is gebaseerd op de autorisatieregels van dat register. 

De policy is beschikbaar in: @@@ nog te bepalen.

> [!NOTE]
> De functionele beschrijving van de toegangscontrole per raadpleging is beschikbaar in de folder **[/raadplegen](/raadplegen/)**

### Notificaties
Met een notificatie wordt een netwerk-deelnemer op de hoogte gebracht door een bronhouder dat er nieuwe (of gewijzigde) informatie is die directe of afgeleide betrekking heeft op die deelnemer. De notificatie bevat informatie die de deelnemer in staat stelt de relevante informatie te raadplegen bij de bron. Een notificatie loopt altijd van bron naar deelnemer.

> [!NOTE]
> De notificaties vanuit het Indicatieregister zijn te vinden in de folder [**/notificaties**](/notificaties/)

## **Raadplegen Indicatieregister**

Het raadplegen van het Indicatieregister is gebonden aan voorwaarden. De raadpleger moet bevoegd zijn én het vastgestelde raadpleegpatroon volgen. Dit patroon is essentieel voor het valideren van de toestemming. 

Als dat patroon niet wordt gevolgd — bijvoorbeeld door ontbrekende autorisatie, onjuiste of incomplete input, of het opvragen van ongeoorloofde gegevens — wordt de toegang geweigerd of het resultaat beperkt.

Use-cases beschrijven hoe een deelnemer het register correct raadpleegt.

### Autorisatieregels en autorisatiematrix
De toegang tot gegevens is vastgelegd doormiddel van **Autorisatieregels** en de **Autorisatiematrix**. De [autorisatieregels](https://informatiemodel.istandaarden.nl/informatiemodel/iwlz/netwerk/indicatieregister-2/regels/autorisatieregel/) zijn te vinden in het Informatiemodel Indicatieregister 2 (via [hier](https://informatiemodel.istandaarden.nl/informatiemodel/iwlz/netwerk/indicatieregister-2/regels/autorisatieregel/)) en de [autorisatiematrix](/raadplegen/autorisatiematrix_indicatieregister.md) is [hier](/raadplegen/autorisatiematrix_indicatieregister.md) te vinden.


> [!NOTE]
> De functionele beschrijving van per raadpleging per deelnemer is beschikbaar in de folder **[/raadplegen](/raadplegen/)**

Meer informatie over de structuur van het raadplegen en het valideren ervan is te lezen in het [Afsprakenstelsel iWlz - Raadplegen](https://wlz.atlassian.net/wiki/x/KgpgAQ)


## Aanvullende Documentatie

### Informatiemodel

![informatiemodel](/src/Informatiemodel-sml.png)

Ondersteunende documentatie is te vinden in het Informatiemodel, via de website [https://informatiemodel.istandaarden.nl/](https://informatiemodel.istandaarden.nl/) en daar de gewenste versie te selecteren (zie ook in de tabel hierboven voor een directe verwijzing).

### GraphQL
![GraphQL](/src/GraphQL-logo-sml.png) 

zie [GraphQL.org](https://graphql.org) 

### Open Agent Policy
![OPA](/src/OPA-logo-sml.png) 

zie [Open Agent Policy](https://www.openpolicyagent.org) en [documentatie](https://www.openpolicyagent.org/docs/latest/)

## Meer informatie
* Actieprogramma iWlz: van keten naar netwerk: [het Actieprogramma iWlz](https://www.istandaarden.nl/iwlz/actieprogramma/index "Over Actieprogramma iWlz")
* Informatiemodel iStandaarden iWlz: [Informatiemodellen](https://informatiemodel.istandaarden.nl)
* Portaal voor iStandaarden in de
Zorg en Ondersteuning: [homepagina iStandaarden](https://www.istandaarden.nl)

## Contactpersonen:
* Dennis de Gouw - [@dennisdegouw](http://github.com/dennisdegouw)
* Remo van Rest - [@rvanrest](https://github.com/rvanrest)


