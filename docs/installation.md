# 1. Installation

## 1.1 Systemvoraussetzungen

Die Nutzung von FluenceScan ist für jeden Windows-Nutzer ohne Weiteres
möglich. Eine NVIDIA-GPU mit CUDA-Unterstützung beschleunigt die
Segmentierung, ist für den Betrieb aber nicht erforderlich - ohne GPU läuft
die Berechnung automatisch auf der CPU (nur langsamer).

!!! note "Installationsgröße (~2 GB)"
    Der Installer dieser Alpha-Version installiert die CUDA/cuDNN-Runtime
    immer mit, unabhängig davon, ob eine NVIDIA-GPU vorhanden ist - daher
    die vergleichsweise große Downloadgröße. Das ist unbedenklich: Ist keine
    kompatible GPU vorhanden, laufen die Berechnungen automatisch und ohne
    weiteres Zutun auf der CPU, die mitinstallierten CUDA-Komponenten bleiben
    dann einfach ungenutzt. Eine schlankere Installationsoption ohne
    CUDA/cuDNN ist für eine künftige Version geplant.

Für die interaktive **Punkt-Klick-Nachsegmentierung** (Kapitel
[2.2](analyse-starten.md#22-auswertung-starten)) ist zusätzlich eine lokale
Python-Installation (Version 3.10 oder höher) mit dem Paket `sam2`
erforderlich:

```bash
pip install "git+https://github.com/facebookresearch/sam2.git"
```

!!! info "Ohne diese Python-Abhängigkeit"
    "Verarbeiten" und "Segmentieren" stehen weiterhin uneingeschränkt zur
    Verfügung - nur die interaktive Nachbearbeitung per Punkt-Klick ist dann
    nicht nutzbar.

## 1.2 Installations-Assistent

Der Windows-Installer (`FluenceScan-Setup-*.exe`) führt durch folgende
Schritte:

1. **Willkommen**
2. **Lizenz** - muss akzeptiert werden, bevor die Installation fortgesetzt
   werden kann
3. **Datenverarbeitung** - hier legst du fest, wie Bilddaten und daraus
    erstellte Labels (klassisch, KI-unterstützt oder per Punkt-Klick
    nachgebessert) behandelt werden:
    - **Automatisch teilen**: Bilddaten und Labels werden automatisch zur
      Modellverbesserung beigetragen
    - **Nur manuell teilen** (Standard): keine automatische Übertragung -
      Daten verlassen deinen Rechner nur, wenn du sie selbst über
      Export exportierst (siehe [2.4](analyse-starten.md#24-speichern-export-contribute))

    **Später änderbar:** Diese Wahl ist keine Voraussetzung für die Nutzung
    der Software und lässt sich jederzeit unter
    [Einstellungen > Beitragen](einstellungen.md#42-beitragen-automatisch-auf-wunsch)
    wieder ändern.

4. **Hinweis zu den Voraussetzungen** (Inhalt siehe [1.1](#11-systemvoraussetzungen))
5. **Installationsverzeichnis** - standardmäßig unter
   `%LocalAppData%\Programs\FluenceScan`, keine Administratorrechte nötig
6. **Zusätzliche Symbole** - optional eine Desktop-Verknüpfung anlegen
7. **Zusammenfassung** und Installation
8. **Fertig** - optional FluenceScan direkt starten

!!! note "Zum mitgelieferten Segmentierungsmodell"
    Der Installer bietet **keine** Auswahl zwischen mehreren
    Segmentierungs-Backends an. Mitgeliefert wird ausschließlich das
    lizenzfreie Meta-SAM2-Referenz-Backend (Apache-2.0). Das optionale,
    AGPL-3.0-lizenzierte Ultralytics-Backend wird bewusst **nicht**
    mitinstalliert - wer es nutzen möchte, bindet es nachträglich über
    [Einstellungen > Segmentierungsmodell > „Eigenes Backend..."](einstellungen.md#41-segmentierungsmodell-wahlen)
    ein.

## 1.3 Erststart

Nach der Installation startet FluenceScan mit leerem Arbeitsbereich. Weiter
geht es mit [Kapitel 2, Analyse starten](analyse-starten.md).
