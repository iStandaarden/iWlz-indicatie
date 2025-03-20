# Query-templates voor het Zorgkantoor

Op dit moment zijn de volgende rollen onderkent:
| Situatie | toelichting |
| :-- |:-- |
 | [Intieel verantwoordelijk Zorgkantoor](#zorgkantoor---initieel-verantwoordelijk) | Een zorgkantoor dat initieel verantwoordelijk is voor de client en zorgt voor de bemiddeling van zorg | 
| [Nieuw verantwoordelijk zorgkantoor](#zorgkantoor---nieuw-verantwoordelijk) | Het zorgkantoor dat de client krijgt overgedragen van het huidige verantwoordelijk zorgkantoor |
| [Uitvoerend zorgkantoor](#zorgkantoor---uitvoerend) | Een zorgkantoor dat bovenregionaal betrokken is bij de uitvoering van zorg | 



## Zorgkantoor - intieel verantwoordelijk

Het zorgkantoor dat verantwoordelijk is voor de regio waarin de client volgens de BRP woont ontvangt de notificiatie Deze notificatie bevat de informatie om de Wlz Indicatie van de client te raadplegen. Naast de ```wlzIndicatieID``` uit de notificatie moeten het eigen ```Uzovicode``` en de datum van oprvagen (```raadpleegdatum```) worden meegegeven.

**Schematisch:**

```mermaid
---
config:
  theme: neutral
  look: classic
---
stateDiagram
    [*] --> Raadplegen
    state idAvailable <<choice>>
    
    Raadplegen --> idAvailable
    idAvailable --> notifyWait: nee
    notifyWait --> notifyReceive
    state chooseQuery <<choice>>
    idAvailable --> chooseQuery: ja
    notifyReceive --> chooseQuery
    chooseQuery --> inputQuery
    inputQuery --> Query
    Query --> [*]
  
    idAvailable: Id's bekend?
    notifyWait: Wacht op notificatie
    notifyReceive: notificatie NIEUWE_INDICATIE_ZORGKANTOOR ontvangen
    inputQuery: wlzIndicatieID, Uzovicode 
    Query: Gebruik query QIR-0001-ZKi

  style notifyWait fill:#FFD600
  style Raadplegen fill:#BBDEFB,color:none
  style notifyReceive,inputQuery fill:#C8E6C9
  style Query fill:#00C853
```

| **Query ID** | **Beschrijving** | **Verplichte input** | **resultaat** | **Autorisatie-regel** |
|---|---|---|---|---|
| [**QIR-0001-ZKi**](/gql-query/zorgkantoor/QIR-0001-ZKi.graphql) | Op basis van de (ontvangen) wlzIndicatieID en eigen identificatie, de bijbehorende WlzIndicatie raadplegen inclusief Clientgegevens | wlzIndicatieID,  Uzovicode, raadpleegdatum | Alle klassen/nodes | [IRA0001](https://informatiemodel.istandaarden.nl/informatiemodel/iwlz/netwerk/indicatieregister-2/regels/autorisatieregel/ira0001/) |

### autorisatieflow en query
Autorisatieflow en query: [QIR-0001-ZKi-autoridatieflow](/gql-query/zorgkantoor/QIR-0001-ZKi-autorisatieflow.md)

## Zorgkantoor - nieuw verantwoordelijk

Na een dossieroverdracht via de registratie van een ```Overdracht``` ontvangt het nieuw verantwoordelijke zorgkantoor de notificatie ```not``` waarmee dat zorgkantoor de informatie kan ophalen met betrekking tot de overdracht. 




## Zorgkantoor - uitvoerend

Query is nog niet beschikbaar doordat het Bemiddelingsregister nog niet volledig in gebruik is. (Uitvoerend zorgkantoor is altijd de bronhouder zelf en anders via ZK33 indicatiegegevens)

---
[Terug naar Query overzicht](/gql-query/README.md)

