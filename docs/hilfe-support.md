# 5. Hilfe & Support

Alle Einträge im Menü **Hilfe** der App im Überblick.

## 5.1 Dokumentation anzeigen

Öffnet dieses Handbuch im Standard-Browser.

## 5.2 Support kontaktieren

Öffnet den Standard-Mail-Client mit vorausgefülltem Empfänger und Betreff,
für Fragen, die über [Fehler melden](#53-afs-auf-github-offnen-fehler-melden)
hinausgehen.

## 5.3 AFS auf GitHub öffnen / Fehler melden

- **AFS auf GitHub öffnen** führt zum öffentlichen Repository
  [Auto-Fluence-Scan-public](https://github.com/Thufir2021/Auto-Fluence-Scan-public).
- **Fehler melden** öffnet direkt das Formular für ein neues Issue dort.

## 5.4 Steuerung & Bedienung (Kurzreferenz)

Ein kompakter In-App-Dialog mit den wichtigsten Handgriffen - Navigation im
Bildstapel, die drei Schritte im Menü Auswertung, der Radierer, Histogramm/
Profillinie sowie Tabelle & Liu-Plot. Dieses Handbuch hier ist die
ausführliche Fassung davon, siehe insbesondere
[Kapitel 2](analyse-starten.md) und [Kapitel 3](zusatzfunktionen.md).

## 5.5 Über FluenceScan

Werkzeug zur Bestimmung der Laser-Schädigungsschwelle (single-shot &
multi-pulse) aus Bildstapeln beschädigter Oberflächen.

- **Methodik**: D²-Methode nach Liu (1982), erweitert um die
  Apertur-Korrektur nach García-Lechuga & Grojo (2021, Open Research
  Europe) und das Inkubationsmodell nach Jee, Becker & Walser (1988).
- **Segmentierung**: Attention-U-Net-Ensemble, optional interaktiv
  nachbesserbar mit SAM2 (Meta).

## 5.6 Lizenz

© 2026 David Karapetyan. Alle Rechte vorbehalten. Die Weitergabe dieser
Software an Dritte ist nur nach vorheriger schriftlicher Vereinbarung mit
dem Urheber gestattet - Details siehe
[LICENSE.txt](https://github.com/Thufir2021/Auto-Fluence-Scan-public/blob/main/LICENSE.txt).

Diese Einschränkung gilt für den von David Karapetyan verfassten Code von
FluenceScan selbst (die Qt-App sowie die Python-Trainings-/Inferenz-Pipeline).
Die unten aufgeführten Drittanbieter-Komponenten sind davon unberührt - sie
bleiben unter ihrer jeweils eigenen, offenen Lizenz und dürfen im Rahmen
dieser Lizenz unabhängig von FluenceScan weiterverwendet werden.

**Trainingsdaten**: Die Trainingsdaten für das Attention-U-Net-
Segmentierungsmodell stammen von Prof. Dr. Klaus Sokolowski-Tinten,
Fakultät für Physik, Universität Duisburg-Essen. Alle Nutzer:innen, die
zur Modellverbesserung beitragen (siehe [4.2](einstellungen.md#42-beitragen-automatisch-auf-wunsch)),
werden ebenfalls dort genannt.

**Mitwirkende**: Über die Trainingsdaten hinaus wird FluenceScan von
weiteren Personen mitentwickelt - Code-Beiträge, Bug-Reports und
Feature-Vorschläge eingeschlossen (siehe [CONTRIBUTING.md](https://github.com/Thufir2021/Auto-Fluence-Scan-public/blob/main/CONTRIBUTING.md)).
Die vollständige, stets aktuelle Liste aller Mitwirkenden führt GitHub
automatisch auf der
[Contributors-Seite](https://github.com/Thufir2021/Auto-Fluence-Scan-public/graphs/contributors)
des Repositories.

**Drittanbieter-Komponenten**:

| Komponente | Zweck in FluenceScan | Lizenz |
|---|---|---|
| SAM2 (Meta) | Standard-Segmentierungs-Backend für Punkt-Klick-Nachbesserung (siehe [1.1](installation.md#11-systemvoraussetzungen), [2.2](analyse-starten.md#22-auswertung-starten)) | Apache License 2.0 |
| Ultralytics | optionales, alternatives Segmentierungs-Backend (nur falls unter [Einstellungen > Segmentierungsmodell](einstellungen.md#41-segmentierungsmodell-wahlen) aktiv ausgewählt) | GNU AGPL-3.0 |
| segmentation-models-pytorch (ResNet-Encoder, ImageNet-vortrainiert) | Netzwerkarchitektur/Encoder des Attention-U-Net-Ensembles | MIT / BSD-3-Clause |
| OpenCV | klassische Bildverarbeitung ohne KI-Modell (Menü Auswertung > „Verarbeiten", siehe [2.2](analyse-starten.md#22-auswertung-starten)) | Apache License 2.0 |
| Qt (dynamisch verlinkt) | grafische Oberfläche der App | GNU LGPLv3 |
| LibTorch / PyTorch | Inferenz (Ausführung) des Attention-U-Net-Segmentierungsmodells | BSD-3-Clause |
| ITK | Bildein-/-ausgabe und -verarbeitung des Bildstapels | Apache License 2.0 |

!!! note "Qt und LGPLv3: warum „dynamisch verlinkt" wichtig ist"
    Die LGPLv3 erlaubt es, Qt in proprietäre Software wie FluenceScan
    einzubinden, solange Qt selbst dynamisch (nicht fest einkompiliert)
    verlinkt bleibt. Praktisch heißt das: Die Qt-Bibliotheken liegen als
    eigene DLL-Dateien neben `FluenceScan.exe` und ließen sich - wie von
    der LGPL gefordert - durch eine kompatible, selbst gebaute Qt6-Version
    ersetzen.

!!! note "Warum Ultralytics nicht mitinstalliert wird"
    AGPL-3.0 ist ein Netzwerk-Copyleft: Wer Software mit AGPL-Bestandteilen
    weitergibt oder öffentlich über ein Netzwerk anbietet, muss unter
    bestimmten Bedingungen auch deren Quellcode offenlegen. Damit
    FluenceScan selbst proprietär bleiben kann, liefert der Installer (siehe
    [1.2](installation.md#12-installations-assistent)) Ultralytics deshalb
    bewusst nicht mit. Wer es trotzdem nutzen möchte, installiert es selbst
    nach (siehe [4.1](einstellungen.md#41-segmentierungsmodell-wahlen)) und
    übernimmt damit für diesen Teil auch die AGPL-Bedingungen.
