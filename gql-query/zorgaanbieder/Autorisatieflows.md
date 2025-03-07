# Autorisatie-flows Zorgaanbieder: QIR-0002-ZA.graphql

**schematisch:**

```mermaid
---
config:
  theme: neutral
  look: classic
---
stateDiagram
  direction TB
  state chooseQuery <<choice>>
  state register {
    direction TB
    notifyWait --> notifyReceive
    notifyReceive --> haalData
    notifyWait
    notifyReceive
    haalData
  }
  state nID {
    direction TB
    state check <<choice>>
    valideren --> check
    check --> checkInput01
    check --> checkInput02
    state check01 <<choice>>
    checkInput01 --> check01
    state check02 <<choice>>
    checkInput02 --> check02
    check01 --> error:nee
    state join_valid <<join>>
    check01 --> join_valid:ja
    check02 --> error:nee
    check02 --> valideer2:ja
    state check11 <<choice>>
    valideer2 --> check11
    check11 --> error:nee
    check11 --> join_valid:ja
    join_valid --> valid
    state check21 <<choice>>
    valid --> check21
    check21 --> error:nee
    check21 --> access:ja
    check
    valideren
    checkInput01
    checkInput02
    check01
    check02
    error
    join_valid
    valideer2
    check11
    valid
    check21
    access
  }
  [*] --> raadplegen
  raadplegen --> idAvailable
  idAvailable --> notifyWait:nee
  idAvailable --> chooseQuery:ja
  haalData --> chooseQuery
  chooseQuery --> inputQuery
  inputQuery --> Query
  Query --> indienen
  indienen --> valideren
  error --> [*]
  access --> resource
  resource --> [*]
  register:Bemiddelingsregister
  notifyWait:Wacht op notificatie
  notifyReceive:notificatie NIEUWE_BEMIDDELINGSPECIFICATIE_ZORGAANBIEDER ontvangen
  haalData:Raadpleeg het bemiddelingsregister voor de wlzIndicatieID
  nID:Autorisatie controle
  valideren:valideer input
  checkInput01:wlzIndicatieID aanwezig?
  checkInput02:agbCode aanwezig?
  error:geen toegang tot Resource
  valideer2:Controleer combinatie agbCode en wlzIndicatieID in Bemiddelingsregiser
  valid:Beide voorwaarden voldoen?
  access:toegeng tot Resource
  raadplegen:Raadplegen Wlz Indicatie
  idAvailable:Id's bekend?
  inputQuery:wlzIndicatieID, Uzovicode
  Query:Gebruik query QIR-0002-ZA
  style notifyWait fill:#FFD600
  style notifyReceive,haalData,inputQuery fill:#C8E6C9
  style error fill:#D50000
  style access,Query,resource fill:#00C853
  style raadplegen fill:#BBDEFB,color:none

```

Controle query
```gql
query Bemiddeling(
  $WlzIndicatieID: UUID!
  $agbCodeInstelling: String!
) {
  bemiddeling(
    where: {
      wlzIndicatieID: { eq: $WlzIndicatieID }
      and: [ {
         bemiddelingspecificatie:  {
            all:  {
               instelling:  {
                  eq: $agbCodeInstelling
               }
            }
         }
      }]
    }
  ) {
      wlzIndicatieID
      bemiddelingspecificatie {
        instelling
      }
    }
  }

```
Als het resultaat overeenkomt met de variabelen meegegeven in de Indicatiequery of als de combi bestaat dan is toegang toegestaan. 

