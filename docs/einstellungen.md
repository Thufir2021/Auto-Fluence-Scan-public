# 4. Einstellungen

## 4.1 Segmentierungsmodell wählen

**Einstellungen > Segmentierungsmodell** listet die verfügbaren
Segmentierungs-Backends als exklusive Auswahl auf. Mitgeliefert wird
standardmäßig nur das lizenzfreie Meta-SAM2-Referenz-Backend
(Apache-2.0, siehe [1.2](installation.md#12-installations-assistent)).

Über **„Eigenes Backend..."** lässt sich ein zusätzliches, selbst
installiertes Backend einbinden (z. B. das optionale, AGPL-3.0-lizenzierte
Ultralytics-Backend) - ein Dateidialog fragt danach das entsprechende
Skript ab.

Die getroffene Wahl gilt für **Segmentieren** und **Punkt-Klick
Nachbessern** gleichermaßen (siehe [2.2](analyse-starten.md#22-auswertung-starten)).

## 4.2 Beitragen: Automatisch ↔ Auf Wunsch

Dieselbe Wahl wie auf der Datenverarbeitungs-Seite des Installers
(siehe [1.2](installation.md#12-installations-assistent)) lässt sich hier
jederzeit ändern:

- **Automatisch**: Bilddaten und erstellte Labels (klassisch,
  KI-unterstützt oder per Punkt-Klick nachgebessert) werden automatisch zur
  Modellverbesserung beigetragen.
- **Auf Wunsch** (Standard): keine automatische Übertragung - Daten
  verlassen dein Gerät nur, wenn du sie selbst über
  **Datei > Export > Contribute** teilst (siehe [2.4](analyse-starten.md#24-speichern-export-contribute)).

!!! note "Was die Übersendung bedeutet"
    Geteilte Daten werden anonymisiert in einer Datenbank gespeichert und
    dienen dem Retraining des aktuellen Segmentierungsmodells - die
    KI-unterstützte Segmentierung liefert damit bislang noch nicht
    durchgehend zufriedenstellende Ergebnisse. Das Teilen hilft also gezielt
    dabei, dieses eigens für Laserphysiker:innen entwickelte
    Segmentierungsmodell zu verbessern.

## 4.3 Sprache ändern

**Einstellungen > Sprache** bietet Systemsprache, Deutsch und English zur
Wahl.

!!! warning "Wirkt erst nach Neustart"
    Ein Sprachwechsel hier wird gespeichert, aber erst beim nächsten Start
    von FluenceScan wirksam.
