# VERWIJDERDE_INDICATIE_ZORGKANTOOR

## Documentatie

Notificatie aan het zorgkantoor als het CIZ een Wlz-indicatie heeft verwijderd waarvoor dit zorgkantoor verantwoordelijk is, was of zou worden.

Het zorgkantoor is daarmee op de hoogte gesteld van de verwijdering van Wlz-indicatie waarvoor dat zorgkantoor verantwoordelijk is, is geweest of door overdracht zou worden. 

## Aanleiding
**De trigger voor de notificatie is:** 

> de verwijdering van een Wlz indicatie in het Indicatieregister

## Instructie
**Stel notificatie op voor:** 
> - het zorgkantoor dat verantwoordelijk is voor de Wlz-indicatie;
> - het zorgkantoor dat verantwoordelijk is geweest voor de Wlz-indicatie;
> - het zorgkantoor dat door overdracht verantwoordelijk zou worden voor de Wlz-indicatie.

## Type
Het type-notificatie: 
> VERPLICHT

## Schematisch

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
trigger:- Verwijderen van
trigger:- Wlz Indicatie
  opstellen:Stel notificatie op voor
opstellen:- alle verantwoordelijke (huidige, verleden, toekomstig)zorgkantoren
opstellen:- VERWIJDERDE_INDICATIE_ZORGKANTOOR
  verstuur:Verstuur 
  verstuur: notificatie
  ontvanger:Verantwoordelijk zorgkantoor
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
| eventType | "VERWIJDERDE_INDICATIE_ZORGKANTOOR" | ```"eventType": "VERWIJDERDE_INDICATIE_ZORGKANTOOR"``` |
| subjectList |  | ```"subjectList": [{```|
| ../subject | "WlzIndicatie/{wlzIndicatieID}" | ```"subject": "WlzIndicatie/ef88ce35-58fa-4e6d-ac7a-6e298dd211d6"``` |
| ../recordID | "WlzIndicatie/{wlzIndicatieID}" | ```"recordID": "WlzIndicatie/ef88ce35-58fa-4e6d-ac7a-6e298dd211d6"``` |
| | | ```}]``` | 



## Andere notificaties Indicatieregister
[Andere notificaties Indicatieregister](README.md)

## Meer informatie over Notificaties

Meer informatie over notificeren in het [Afsprakenstelsel iWlz](https://wlz.atlassian.net/wiki/x/5AlgAQ?atlOrigin=eyJpIjoiNzMyN2E3MjM3YjQwNGQ4MmFkZDgwNWY0ZmE0MDIzMGEiLCJwIjoiYyJ9): [link](https://wlz.atlassian.net/wiki/x/5AlgAQ?atlOrigin=eyJpIjoiNzMyN2E3MjM3YjQwNGQ4MmFkZDgwNWY0ZmE0MDIzMGEiLCJwIjoiYyJ9)

