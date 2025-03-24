# Autorisatie-flows Zorgaanbieder: QIR-0002-ZA.graphql

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
    check01 --> valideer2:ja
    valideer2 --> valid
    state check21 <<choice>>
    valid --> check21
    check21 --> error:nee
    check21 --> access:ja

  }

  error --> [*]
  access --> resource
  resource --> [*]
  
  nID:Autorisatie controle PEP
  indienen: Ontvang QIR-0002-ZA + Access token
  validerenT: Valideer access token
  validerenR: Valideer Request
  checkInput01:wlzIndicatieID aanwezig?
  error:geen toegang tot Resource
  valideer2:Controleer combinatie agbCode (uit token) en wlzIndicatieID (uit Query) in Bemiddelingsregiser
  valid: Juist resultaat controle?
  access:toegeng tot Resource
  resource: Query mag door naar Indicatieregister
  style validerenT,validerenR fill:#FFD600
  style valideer2 fill:#C8E6C9
  style error fill:#D50000
  style access,Query,resource fill:#00C853
  style indienen fill:#BBDEFB,color:none

```

**Controle query PIP:**
```gql
query Bemiddeling(
  $WlzIndicatieID: UUID! # uit query
  $agbCodeInstelling: String! # uit Accestoken
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

---
[Terug naar Query overzicht](/gql-query/README.md)