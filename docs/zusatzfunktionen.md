# 3. Zusatzfunktionen

## 3.1 Proben-Anordnung (Sample Layout)

**Ansicht > Proben-Anordnung anzeigen...** öffnet ein eigenes Fenster, das
alle Aufnahmen lückenlos in ihrer tatsächlichen Anordnung zeigt - je nach
gewähltem Ansichts-Modus:

- **Serie**: eine Reihe (ein Bild pro Energie)
- **Array (Matrix)**: Zeilen/Spalten entsprechend der `_R<n>/_C<n>`-Angaben
  im Dateinamen
- Ein Array bedeutet dabei: Es wird angenommen, dass mehrere Spots mit
  derselben Energie bestrahlt wurden. Die Pulsenergien aller Spots eines
  Energielevels werden gemittelt, ebenso die resultierenden Flächen dieser
  Spots - aus beidem entsteht je ein gemittelter Energie- und Flächenwert
  pro Energielevel, mit dem die Liu-Auswertung funktioniert. Dazu mehr im
  [Anhang, A.4](anhang.md#a4-mittelung-gleicher-energien-im-array-modus).

Der Ansichts-Modus selbst wird oberhalb im Menü **Ansicht** festgelegt
(„Automatisch", „Serie", „Array (Matrix)") - die Proben-Anordnung ist davon
unabhängig auch in „Serie" nutzbar, um kurz alle Aufnahmen nebeneinander zu
sehen.

## 3.2 Histogramm & Profillinie

**Ansicht > Histogramm anzeigen** blendet ein Profil-/Objektgrenzen-Panel
ein oder aus.

**Ansicht > Profillinie anzeigen** aktiviert einen Modus, in dem sich die
Linie im Bild per Maus-Drag verschieben lässt - sie legt fest, aus welcher
Bildzeile das Histogramm berechnet wird (standardmäßig die Bildmitte).

!!! note "Schließt sich mit Punkt-Klick Nachbessern aus"
    Profillinie und [Punkt-Klick Nachbessern](analyse-starten.md#22-auswertung-starten)
    sind exklusive Modi - wird der eine aktiviert, schaltet sich der andere
    automatisch ab. Der Radierer (Strg+Klick) bleibt in beiden Fällen
    zusätzlich nutzbar.
