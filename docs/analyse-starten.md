# 2. Analyse starten

Die Auswertung der Fluenzschwellenwerte soll mit FluenceScan vereinfacht
werden. Die Liu-Auswertung ist dabei in drei Schritten erledigt:

1. Aufnahmen der Laserspots und die für jeden Spot verwendeten Pulsenergien
   öffnen
2. Segmentierung starten
3. Bei Bedarf per Punkt-Klick nachbessern

Die folgenden Abschnitte gehen diese drei Schritte im Detail durch.

## 2.1 Bildstapel & Energien laden

**Datei > Bildstapel laden** öffnet einen Ordnerdialog und lädt alle
enthaltenen Aufnahmen als Stapel. FluenceScan erkennt aus den Dateinamen
automatisch, ob es sich um eine **Serie** (ein Bild pro Energie, für die
klassische Liu-Auswertung) oder ein **Array** (mehrere Spots je Energie,
Zeilen/Spalten aus `_R<n>/_C<n>` im Dateinamen) handelt. Die Erkennung lässt
sich unter **Ansicht** jederzeit manuell auf „Serie" oder „Array (Matrix)"
umstellen, falls „Automatisch" danebenliegt.

**Datei > Energien laden (.csv/.txt)** ordnet jedem Bild im Stapel die
zugehörige Pulsenergie zu - Voraussetzung für die automatische Auswertung
in [2.3](#23-ergebnis-liu-auswertung-tabelle-diagramm).

!!! tip "Zuletzt geöffnet"
    **Datei > Zuletzt geöffnet** merkt sich zuletzt geladene Bildstapel für
    den schnellen Wiedereinstieg.

## 2.2 Auswertung starten

Im Menü **Auswertung** stehen drei Schritte zur Verfügung. Sie bauen
inhaltlich aufeinander auf, sind aber **unabhängig voneinander aufrufbar** -
du kannst direkt mit KI-Segmentierung starten, ohne vorher klassisch zu
verarbeiten, und direkt zur Punkt-Klick-Nachbesserung springen, ohne vorher
zu segmentieren:

1. **Verarbeiten** - klassische Bildverarbeitung/Segmentierung ohne
   KI-Modell.
2. **Segmentieren** - automatische, KI-gestützte Segmentierung. Welches
   Modell dabei verwendet wird, legst du unter
   [Einstellungen > Segmentierungsmodell](einstellungen.md#41-segmentierungsmodell-wahlen)
   fest.
3. **Punkt-Klick Nachbessern** - Modus aktivieren, dann per Linksklick auf
   ein Objekt im Bild klicken, um es nachzusegmentieren; die Änderung wirkt
   sofort. Rechtsklick macht den letzten Klick rückgängig. Ein grüner Haken
   erscheint nach der ersten Korrektur und sperrt die aktuellen Konturen
   gegen Ersetzen, damit ein weiterer Klick einen zweiten Spot ergänzt,
   statt den ersten zu überschreiben.

!!! tip "Radierer (immer aktiv)"
    Mit **Strg+Klick** kann eine ungewünschte Kontur im Bild gelöscht
    werden.

## 2.3 Ergebnis: Liu-Auswertung, Tabelle & Diagramm

Sobald Konturen vorliegen (aus 2.2, in beliebiger Kombination der drei
Schritte) und Energien geladen sind (aus 2.1), aktualisieren sich **Tabelle
und Liu-Diagramm automatisch** - die eigentliche Liu-Auswertung ist damit
bereits fertig, ganz ohne einen separaten „Auswerten"-Klick.

- **Haupttabelle**: Auf eine Spot-Spaltenüberschrift (A₁/A₂) klicken, um
  zwischen Fläche und r₀² umzuschalten.
- **Meta-Tabelle**: `N_Pulses` und `S` (Inkubationskoeffizient, 0-1) für das
  Mehrpuls-Modell nach
  [Jee, Becker & Walser (1988)](https://doi.org/10.1364/JOSAB.5.000648)
  eintragen, um F_th(1) zu berechnen.
- **GLG-Aperturkorrektur** (optional zuschaltbar): korrigiert die
  Liu-Auswertung um Faktoren, die einem echten Laserprofil entsprechen,
  statt der Annahme eines idealen Gauß-Profils - dafür muss die
  Transmission der Kreisblende in Fokalposition bekannt sein. Zieht eine
  korrigierte Gerade parallel zum Liu-Fit in Tabelle und Diagramm nach.

Die physikalischen Hintergründe beider Modelle sind im
[Anhang](anhang.md) beschrieben.

## 2.4 Speichern & Export / Contribute

Alle Ergebnisse lassen sich unter **Datei > Export** einzeln sichern:

| Export-Eintrag | Inhalt |
|---|---|
| Labels | Konturen aus Segmentierung (Masken) |
| Koordinaten | Pixelkoordinaten aller Konturpunkte, jedes Spots, jedes Bilds im Stapel, als CSV |
| Tabelle | Haupt- und Meta-Tabelle als eine CSV-Datei |
| Diagramm | das Liu-Diagramm als Bilddatei |
| Projekt | das gesamte Projekt (Bildstapel + Energien + Labels + Tabellenwerte) als Projekt-Bundle |
| Contribute | Bilddaten + finale Labels/Masken als Bundle, zur Weitergabe an die Entwicklung |

**Datei > Projekt öffnen** lädt ein zuvor exportiertes Projekt-Bundle
wieder vollständig ein.

!!! note "Contribute ist (noch) ein manueller Versand"
    „Contribute" exportiert das Bundle lokal - eine automatische
    Serverübertragung gibt es aktuell nicht. Das Bundle schickst du danach
    selbst (z. B. per E-Mail) an die Entwicklung, siehe
    [Support kontaktieren](hilfe-support.md#52-support-kontaktieren). Ob
    Contribute automatisch bei jeder Auswertung vorgeschlagen wird oder nur
    auf Wunsch, legst du unter
    [Einstellungen > Beitragen](einstellungen.md#42-beitragen-automatisch-auf-wunsch)
    fest.

Weiter geht es mit [Kapitel 3, Zusatzfunktionen](zusatzfunktionen.md).
