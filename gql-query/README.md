# GraphQL-query templates Bemiddelingsregister
Hier staan de query templates die een raadpleger kan gebruiken voor het raadplegen van gegevens in het Bemiddelingsregister. De templates dienen als voorbeeld hoe de query opgebouwd moet worden. De structuur en bepaalde verplichte parameters zijn nodig om te voldoen aan de autorisatie-policies. Doet een raadpleger dat niet dan kan de vraag niet afgehandeld worden. Bijvoorbeeld doordat de raadpleger benodigde input vergeet mee te geven, gegevens wil raadplegen die niet horen bij de raadpleger of omdat er meer gegevens worden geraadpleegd dan is toegestaan op dat moment. 

Een vraag wordt gesteld door een actor als deelnemer van het netwerk. Deze deelnemer stelt de vraag vanuit een bepaalde autorisatie. Afhankelijk van de autorisatie zijn gegevens wel of niet (direct) raadpleegbaar. 

Op dit moment zijn de volgende rollen onderkent:
| Deelnemer | rol | toelichting |
| :-- | :-- |:-- |
| Zorgaanbieder | [uitvoerend](#zorgaanbieder---uitvoerend) | Een zorgaanbieder die betrokken is bij de uitvoering van zorg |
| Zorgkantoor | [intieel verantwoordelijke](#zorgkantoor---initieel-verantwoordelijk) | Een zorgkantoor dat initieel verantwoordelijk is voor de client en zorgt voor de bemiddeling van zorg | 
| Zorgkantoor | [nieuw verantwoordelijk](#zorgkantoor---nieuw-verantwoordelijk) | Het zorgkantoor dat de client krijgt overgedragen van het huidige verantwoordelijk zorgkantoor |
_De lijst is nog niet volledig._


## Beschikbare templates per rol

### Zorgaanbieder - uitvoerend
nog geen queries

### Zorgkantoor - intieel verantwoordelijk
Na de ontvangst van de notificatie *```NIEUWE_INDICATIE_ZORGKANTOOR```*

| **Query ID** | **Beschrijving** | **Verplichte input** | **resultaat** | **Autorisatie** |
|---|---|---|---|---|
| [**QIR-0001-ZKi**](/gql-query/zorgkantoor/QIR-0001-ZKi.graphql) | Op basis van de (ontvangen) wlzIndicatieID en eigen identificatie, de bijbehorende WlzIndicatie raadplegen inclusief Clientgegevens | bemiddelingspecificatieID (V),  Uzovicode (V), raadpleegdatum | Alle klassen/nodes | IRA0001 |

### Zorgkantoor - nieuw verantwoodelijk
nog geen queries
