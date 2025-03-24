# NIEUWE_INDICATIE_ZORGKANTOOR

## Documentatie

Notificatie aan het zorgkantoor als het CIZ een nieuwe Wlz-indicatie heeft geregistreerd voor een cliënt die in de regio van dit zorgkantoor woont.

Het zorgkantoor is daarmee op de hoogte gesteld van de aanwezigheid van een nieuwe Wlz-indicatie voor een client die volgens het BRP woonachtig is in de regio waarvoor dat zorgkantoor verantwoordelijk is. De notificatie bevat informatie waarmee dat zorgkantoor de Wlz-indicatie kan raadplegen.

## Aanleiding
**De trigger voor de notificatie is:** 

> de registratie van een Wlz indicatie in het Indicatieregister

## Instructie
**Stel notificatie op voor:** 
> - het zorgkantoor van de regio waarin de client volgens zijn BRP-adres woont. Als er geen BRP-adres is, stel dan notificatie op voor: het zorgkantoor van de regio waarin de client volgens zijn verblijfadres woont

## Type
Het type-notificatie: 
> VERPLICHT


```mermaid
---
config:
  theme: neutral
  look: classic
---
stateDiagram
  direction LR
  state verzender {
    direction TB
    trigger --> opstellen
    opstellen --> verstuur
    trigger
    opstellen
    verstuur
  }
  state ontvanger {
    direction TB
    ontvang --> verwerk
    ontvang
    verwerk
  }
  [*] --> trigger
  verstuur --> ontvang
  verwerk --> [*]
  verzender:CIZ
  trigger:Trigger
trigger:- Registratie van
trigger:- nieuwe Wlz Indicatie
  opstellen:Stel notificatie op voor
opstellen:- initieel verantwoordelijk zorgkantoor
opstellen:- NIEUWE_INDICATIE_ZORGKANTOOR
  verstuur:Verstuur 
  verstuur: notificatie
  ontvanger:Initieel verantwoordelijk zorgkantoor
  ontvang:Ontvang 
  ontvang:notificatie
  verwerk:Verwerk 
  verwerk:notificatie

```


## Inhoud van de notificatie

| Variabele | Waarde | Voorbeeld | 
| :-- | :-- | :-- |
| timestamp | {timestamp} | ```"timestamp": "2024-07-02T00:00:00Z"``` | 
| afzenderIDType | "KVK" | ```"afzenderIDType": "KVK"``` |
| afzenderID | "62253778" | ```"afzenderID": "62253778"``` |
| ontvangerIDType | "UZOVI" | ```"ontvangerIDType": "UZOVI"``` |
| ontvangerID | {uzovi-code ontvanger} | ```"ontvangerID": "5151"``` |
| ontvangerKenmerk | NULL | |
| eventType | "NIEUWE_INDICATIE_ZORGKANTOOR" | ```"eventType": "NIEUWE_INDICATIE_ZORGKANTOOR"``` |
| subjectList |  | ```"subjectList": [{```|
| ../subject | "WlzIndicatie/{wlzIndicatieID}" | "subject": "WlzIndicatie/ef88ce35-58fa-4e6d-ac7a-6e298dd211d6"|
| ../recordID | "WlzIndicatie/{wlzIndicatieID}" | "recordID": "WlzIndicatie/ef88ce35-58fa-4e6d-ac7a-6e298dd211d6" |
| | | ```}``` | 



## Andere notificaties Indicatieregister
[Andere notificaties Indicatieregister](README.md)

## Meer informatie over Notificaties

Meer informatie over notificeren in het [Afsprakenstelsel iWlz](https://wlz.atlassian.net/wiki/x/5AlgAQ?atlOrigin=eyJpIjoiNzMyN2E3MjM3YjQwNGQ4MmFkZDgwNWY0ZmE0MDIzMGEiLCJwIjoiYyJ9): [link](https://wlz.atlassian.net/wiki/x/5AlgAQ?atlOrigin=eyJpIjoiNzMyN2E3MjM3YjQwNGQ4MmFkZDgwNWY0ZmE0MDIzMGEiLCJwIjoiYyJ9)

