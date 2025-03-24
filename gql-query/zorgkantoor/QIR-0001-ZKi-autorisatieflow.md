# Autorisatie-flow Zorgkantoor: QIR-0001-ZKi.graphql

Beschrijving van het autorisatieproces door de PEP.

**schematisch:**

```mermaid
---
config:
  theme: neutral
  look: classic
---
stateDiagram
  direction TB
  [*] -->  indienen
  indienen --> validerenT
  state nID {
    direction TB

    validerenT --> validerenR
    validerenR --> checkInput01


    state check01 <<choice>>
    checkInput01 --> check01
    check01 --> error:nee
    check01 --> access:ja
   

  }

  error --> [*]
  access --> resource
  resource --> [*]
  
  nID:Autorisatie controle PEP
  indienen: Ontvang QIR-0002-ZA + Access token
  validerenT: Valideer access token
  validerenR: Valideer Request
  checkInput01:wlzIndicatieID + Uzovicode aanwezig?
  error:geen toegang tot Resource

  access:toegeng tot Resource
  resource: Query mag door naar Indicatieregister
  style validerenT,validerenR fill:#FFD600
  style valideer2 fill:#C8E6C9
  style error fill:#D50000
  style access,Query,resource fill:#00C853
  style indienen fill:#BBDEFB,color:none

```

Controle query PIP:
```gql
niet van toepassing

```


---
[Terug naar Query overzicht](/gql-query/README.md)