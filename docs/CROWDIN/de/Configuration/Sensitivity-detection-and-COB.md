# Empfindlichkeitserkennung

## Sensitivitäts-Algorithmus

Aktuell gibt es drei Modelle zur Empfindlichkeitserkennung:

* Sensitivität Oref0
* Sensitivität AAPS
* Durchschnittliche Sensitivität
* Sensitivität Oref1

### Sensitivity Oref0

Grundsätzlich wird die Sensitivität auf Basis der Daten der vorangegangenen 24 Stunden berechnet. Kohlenhydrate (falls noch nicht absorbiert) werden nach einer bestimmten Zeit, die man einstellen kann, einfach abgeschnitten. Der Algorithmus ähnelt OpenAPS Oref0, beschrieben in der [OpenAPS Oref0 Dokumentation](https://openaps.readthedocs.io/en/2017-05-21/docs/walkthrough/phase-4/advanced-features.html).

### Sensitivity AAPS

Die Empfindlichkeit wird wie bei Oref0 berechnet, aber du kannst einstellen wie weit der Algorithmus in die Vergangenheit "schaut". Die minimale Kohlenhydrat-Absorption wird ausgehend von der maximalen Kohlenhydrat-Absorption berechnet, die in den Einstellungen festgelegt werden kann

### Durchschnittliche Sensitivität

Die Empfindlichkeit wird als gewichtetes Mittel der Schwankungen berechnet. Neuere Schwankungen haben ein größeres Gewicht. Die minimale Kohlenhydrat-Absorption wird ausgehend von der maximalen Kohlenhydrat-Absorption berechnet, die in den Einstellungen festgelegt werden kann. Dieser Algorithmus berücksichtigt Empfindlichkeitsveränderungen am schnellsten.

### Sensitivität Oref1

Die Sensitivität wird auf Basis der Daten der vergangenen 8 Stunden oder seit dem letzten Katheterwechsel berechnet, falls er weniger als 8 Stunden her ist Kohlenhydrate (falls noch nicht absorbiert) werden nach der in den Einstellungen festgelegten Zeit abgeschnitten. Only the Oref1 algorithm supports un-announced meals (UAM). Das heißt, Zeiten mit erkannten UAM werden bei der Sensitivitätsberechnung nicht berücksichtigt. Wenn du also SMB mit UAM verwendest, dann musst du den Oref1 Algorithmus auswählen, damit es gut läuft. Für weitere Informationen lies die [OpenAPS Oref1 Dokumentation](https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/autosens.html).

## COB Beispiele

Oref0 / Oref1 - nicht absorbierte Kohlenhydrate werden nach der eingestellten Zeit abgeschnitten

![COB nach oref0](../images/cob_oref0.png)

AAPS, Durchschnittliche Sensitivität - Absorption wird so berechnet, dass nach der vorgegeben Zeit `COB == 0` gilt

![COB nach AAPS](../images/cob_aaps.png)

Falls die minimale Kohlenhydrat-Absorption statt einem aus den Schwankungen berechneten Wert genutzt wird, wird in der COB-Kurve ein grüner Punkt angezeigt