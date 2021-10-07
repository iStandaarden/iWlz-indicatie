# Changelog
Alle noemenswaardige wijzigingen zullen worden vastgelegd in dit document. 
Kies een versie voor een uitgebreide vergelijking met de voorgaande versie.

---
## [Unreleased]
- Diverse clean-ups en fixes: Zie [commit-history]

## [v0.9.7] - 2021-10-07
- typo fix
- enumeratie fix
- consistentie tussen IO31.xsd en koppelvlak
- aanvulling GraphQL met WZD informatie
- Issue #22 - [link](https://github.com/iStandaarden/iWlz-indicatie/issues/22)

## [v0.9.6] - 2021-08-25
### Aangepast
- Alle GET operaties gewijzingd naar POST operaties: Issue #11 [link](https://github.com/iStandaarden/iWlz-indicatie/issues/11)

### Toegevoegd
- relatieNummer aan Contactpersoon voor overgang xsd naar register
## [v0.9.5] - 2021-04-30
### Algemeen
- Issue #8 - [link](https://github.com/iStandaarden/iWlz-indicatie/issues/8)
- Issue #4 - [link](https://github.com/iStandaarden/iWlz-indicatie/issues/4)

### Toegevoegd 
- GRAPHQL-schema specificatie
- CHANGELOG file
- elementen WZD toegevoegd aan Client
- enum COD0824

### Aangepast
- Bij opvragingen via wlzindicatieID de error omschrijvingen:
    - "404 Geen xxxxxx gevonden" omzetten naar "404 Onbekend WLZ indicatie ID".
    - "400 Ongeldig ID" omzetten naar "400 Ongeldig WLZ indicatie ID"
- Losse bevragingen Bopz en Wzd onder bevraging via indicatieiD gebracht
- correcties op codelijsten: COD366, COD478, COD046
- X-PSID gewijzigd in string ipv integer

### Verwijderd
- aparte bevraging BeperkingScores

## [v0.9.4] - 2021-03-19
### Algemeen
- Issue #5 - [link](https://github.com/iStandaarden/iWlz-indicatie/issues/5)

### Toegevoegd 
- 

### Aangepast
- fixed tag names
- fixed spelling en casing 

### Verwijderd
- Removed object wrapper around WlzindicatieID

## [v0.9.3] - 2021-02-03
### Algemeen
- Opmerkingen review Menzis d.d. 29-10-2020 verwerkt
- Opmerkingen review CIZ d.d. 09-11-2020 verwerkt

### Toegevoegd
- verwijzing naar OpenApi documentatie
- communicatievorm
- grondslag

### Aangepast
- x-entiteit gewijzigd naar x-requestId

### Verwijderd
- Abonnementen Indicatieregister verplaatst naar Generiek (abonnementen) koppelvlakspecificatie - [Link](https://github.com/iStandaarden/iWlz-generiek)
- Minimale en maximale lengte restricties bij aanwezigheid van pattern-restricties of enum.

## [v0.9.2] - 2020-10-27
### Algemeen
- Opmerking review CIZ d.d. 23-12-2019 verwerkt
- Mogelijkheid om Wzd of BOPZ te vinden voor Bsn
- Datamodel aangepast

### Toegevoegd
- Preview in SwaggerUI
- BOPZ en WZD request

### Aangepast
- 

### Verwijderd
- 

## [v0.9.1.5] - 2019-10-03
### Algemeen
- Release voor POC deelnemers
- Opmerkingen review CIZ verwerkt
- Abonnement opgesplits naar 
    - abonnement op indicaties voor een specifieke organisatie
    - abonnement op indicaties voor een specifieke persoon
- Abonnement Callback gespecificeerd 

## [v0.9.1.4] - 2019-09-10 - Initiële Github versie
### Algemeen
- v0.9.1.4 - version for internal review by CIZ projectteam
Herziening versioning (was voorheen v1.4)
- eerste versie in Github. 

[unreleased]: https://github.com/iStandaarden/iWlz-indicatie/compare/v0.9.7...master
[commit-history]: https://github.com/iStandaarden/iWlz-indicatie/compare/v0.9.7...master
[v0.9.8-pre]: https://github.com/iStandaarden/iWlz-indicatie/compare/v0.9.7...v0.9.8-pre
[v0.9.7]: https://github.com/iStandaarden/iWlz-indicatie/compare/v0.9.6...v0.9.7
[v0.9.6]: https://github.com/iStandaarden/iWlz-indicatie/compare/v0.9.5...v0.9.6
[v0.9.5]: https://github.com/iStandaarden/iWlz-indicatie/compare/v0.9.4...v0.9.5
[v0.9.4]: https://github.com/iStandaarden/iWlz-indicatie/compare/v0.9.3...v0.9.4
[v0.9.3]: https://github.com/iStandaarden/iWlz-indicatie/compare/v0.9.2...v0.9.3
[v0.9.2]: https://github.com/iStandaarden/iWlz-indicatie/compare/v0.9.1.5...v0.9.2
[v0.9.1.5]: https://github.com/iStandaarden/iWlz-indicatie/compare/v0.9.1.4...v0.9.1.5
[v0.9.1.4]: https://github.com/iStandaarden/iWlz-indicatie/releases/tag/v0.9.1.4

---
The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).
