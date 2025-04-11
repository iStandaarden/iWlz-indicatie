# GraphQL-query templates Indicatieregister
Hier staan de query templates die een raadpleger kan gebruiken voor het raadplegen van gegevens in het Indicatieregister. De templates dienen als voorbeeld hoe de query opgebouwd moet worden. De structuur en bepaalde verplichte parameters zijn nodig om te voldoen aan de autorisatie-policies. Doet een raadpleger dat niet dan kan de vraag niet afgehandeld worden. Bijvoorbeeld doordat de raadpleger benodigde input vergeet mee te geven, gegevens wil raadplegen die niet horen tot de raadpleger of omdat er meer gegevens worden geraadpleegd dan is toegestaan op dat moment. 

Een vraag wordt gesteld door een actor als deelnemer van het netwerk. Deze deelnemer stelt de vraag vanuit een bepaalde autorisatie. Afhankelijk van de autorisatie zijn gegevens wel of niet (direct) raadpleegbaar. 

> [!NOTE]
> Informatie over het raadplegen en de bijbehorende toegangscontrole van het indicatieregister door een actor is te lezen onder **[RAADPLEGEN](/raadplegen/README.md)**.
> 


## Beschikbare templates per rol

Op dit moment zijn de volgende rollen onderkent:
| Deelnemer  rol | toelichting | query |
| :-- | :-- |:-- |
| **Zorgaanbieder** - uitvoerend | Een zorgaanbieder die betrokken is bij de uitvoering van zorg | [QIR-0002-ZA.graphql](/gql-query/zorgaanbieder/QIR-0002-ZA.graphql) |
| **Zorgkantoor** - initieel verantwoordelijk | Een zorgkantoor dat initieel verantwoordelijk is voor de client en zorgt voor de bemiddeling van zorg | [QIR-0001-ZKi.graphql](/gql-query/zorgkantoor/QIR-0001-ZKi.graphql) |
| **Zorgkantoor** - nieuwe verantwoordelijk | Het zorgkantoor dat de client krijgt overgedragen van het huidige verantwoordelijk zorgkantoor | [QIR-0003-ZKn.graphql](/gql-query/zorgkantoor/QIR-0003-ZKn.graphql) |
| **Zorgkantoor** - bovenregionaal | Een zorgkantoor dat bovenregionaal betrokken is bij de uitvoering van zorg | [QIR-0004-ZKu.graphql](/gql-query/zorgkantoor/QIR-0004-ZKu.graphql) |

Kies een rol voor de beschikbare query-templates. 

---
Terug naar [HOME](/README.md)