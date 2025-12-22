# Raadplegen Indicatieregister

Het raadplegen van het Indicatieregister is gebonden aan voorwaarden. De raadpleger moet bevoegd zijn én het vastgestelde raadpleegpatroon volgen. Dit patroon is essentieel voor het valideren van de toestemming. 

Als het patroon niet wordt gevolgd — bijvoorbeeld door ontbrekende autorisatie, onjuiste of incomplete input, of het opvragen van ongeoorloofde gegevens — wordt de toegang geweigerd of het resultaat beperkt.

Use-cases beschrijven hoe een deelnemer het register correct raadpleegt.

Meer informatie over de structuur van het raadplegen en het valideren ervan is te lezen in het [Afsprakenstelsel iWlz - Raadplegen](https://wlz.atlassian.net/wiki/x/KgpgAQ)


## Use-cases raadplegen Indicatieregister

De use-cases voor het raadplegen van het Indicatieregister per rol en bijbehorende beschrijving van de toegangscontrole door de PDP[^1]. 

```mermaid
---
config:
  theme: mc
  look: classic
  layout: elk
---
flowchart LR
 subgraph s1["PDP"]
          P["toegangscontrole"]
 end
 subgraph s2["Indicatieregister"]
          B["Resource"]
  end
    A["Raadpleger"] --> R
    R["Use-case<br>Raadplegen"] --> P
    P --> B
    B@{ shape: terminal}
    P@{ shape: terminal}
    A@{ shape: rounded}
    R@{ shape: rounded}
    
```

Kies een use-case voor de beschrijving van het raadplegen of controleren van de toegang van die raadpleging.

### Zorgaanbieder

| Doel | toelichting | raadplegen | toegangscontrole |
| :-- |:-- | :-- | :-- |
| Wlz Indicatie raadplegen | **Als** zorgaanbieder die betrokken is bij het leveren van zorg, **wil ik** de Wlz Indicatie raadplegen van de client waar ik een bemiddelingsspecificatie heb, **zodat** ik inzicht heb in de geïndiceerde zorg  | [UCIR-0002-raadplegen](/raadplegen/zorgaanbieder/UCIR-0002-raadplegen.md) | [UCIR-0002-toegangscontrole](/raadplegen/zorgaanbieder/UCIR-0002-toegangscontrole.md) |


### Zorgkantoor

| Doel | toelichting | raadplegen | toegangscontrole |
| :-- |:-- | :-- | :-- |
|  Wlz Indicatie raadplegen door **Initieel** verantwoordelijk zorgkantoor | **Als** zorgkantoor dat initieel verantwoordelijk is voor de client en zorgt voor de bemiddeling van zorg, **wil ik** de Wlz Indicatie raadplegen van de client, **zodat** ik inzicht heb in de geïndiceerde zorg. | [UCIR-0001-raadplegen](/raadplegen/zorgkantoor/UCIR-0001-raadplegen.md) | [UCIR-0001-toegangscontrole](/raadplegen/zorgkantoor/UCIR-0001-toegangscontrole.md) | 
|  Wlz Indicatie raadplegen na dossieroverdracht | **Als** zorgkantoor dat de client krijgt overgedragen van het huidige verantwoordelijk zorgkantoor , **wil ik** de Wlz Indicatie raadplegen van de client, **zodat** ik inzicht heb in de geïndiceerde zorg. | [UCIR-0003-raadplegen](/raadplegen/zorgkantoor/UCIR-0003-raadplegen.md) | [UCIR-0003-toegangscontrole](/raadplegen/zorgkantoor/UCIR-0003-toegangscontrole.md) |
|  Wlz Indicatie raadplegen bovenregionaal betrokken | **Als** zorgkantoor dat bovenregionaal betrokken is bij de uitvoering van zorg , **wil ik** de Wlz Indicatie raadplegen van de client, **zodat** ik inzicht heb in de geïndiceerde zorg. | [UCIR-0004-raadplegen](/raadplegen/zorgkantoor/UCIR-0004-raadplegen.md) | [UCIR-0004-toegangscontrole](/raadplegen/zorgkantoor/UCIR-0004-toegangscontrole.md) | 
| WlzIndicatieID opvragen | **Als** zorgkantoor dat door dossieroverdracht via het berichtenverkeer (ZK31) een client krijgt overgedragen, **wil ik** de WlzIndicatieID raadplegen van de client, **zodat** ik de client kan bemiddelen | [UCIR-0005-raadplegen](/raadplegen/zorgkantoor/UCIR-0005-raadplegen.md) | [UCIR-0005-toegangscontrole](/raadplegen/zorgkantoor/UCIR-0005-toegangscontrole.md) | 


[^1]: PDP: Policy Decision Point. [Afsprakenstelsel iWlz - Raadplegen](https://wlz.atlassian.net/wiki/x/KgpgAQ)

---
Terug naar [HOME](/README.md)
