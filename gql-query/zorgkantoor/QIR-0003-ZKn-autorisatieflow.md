# Autorisatie-flows Zorgaanbieder: QIR-0003-ZKn.graphql

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
  indienen: Ontvang QIR-0003-ZKn + Access token
  validerenT: Valideer access token
  validerenR: Valideer Request
  checkInput01:wlzIndicatieID aanwezig?
  error:geen toegang tot Resource
  valideer2:PIP
  valideer2:Controleer combinatie uzovicode (uit token) en 
  valideer2:wlzIndicatieID (uit Query) in Bemiddelingsregister
  valid: Juist resultaat controle?
  access:toegang tot Resource
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
  $uzovicodeNieuwzorgkantoor: String! # uit Accestoken
) {
  overdracht(
    where: {
      verantwoordelijkZorgkantoor: { eq: $uzovicodeNieuwzorgkantoor }
      and: [ {
         bemiddeling:  {
            and:  {
               wlzIndicatieID:  {
                  eq: $WlzIndicatieID
               }
            }
         }
      }]
    }
  ) {
      verantwoordelijkZorgkantoor
      bemiddeling {
        wlzIndicatieID
      }
    }
  }

```
Als het resultaat overeenkomt met de variabelen meegegeven in de Indicatiequery of als de combi bestaat dan is toegang toegestaan. 

---
[Terug naar Query overzicht](/gql-query/README.md)