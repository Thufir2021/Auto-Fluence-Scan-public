# A. Anhang: Die Physik dahinter

Die übrigen Kapitel dieses Handbuchs sind bewusst **operativ** gehalten: Sie
erklären, wo du in der App klickst und was dabei passiert - nicht, warum es
funktioniert. Dieser Anhang holt das nach und beschreibt die Physik und
Mathematik hinter der Liu-Auswertung, dem Mehrpuls-Modell und der
GLG-Aperturkorrektur.

## A.1 Die D²-Methode nach Liu (1982)

FluenceScan geht von einem (näherungsweise) gaußförmigen Strahlprofil aus:
Die Fluenz F an einem Punkt im Abstand r von der Strahlmitte ergibt sich aus
der Spitzenfluenz F₀ als

```
F(r) = F₀ · exp(-2r² / w₀²)
```

mit w₀ als Strahlradius (1/e²). Eine sichtbare Veränderung der Oberfläche
(Ablation, Schmelzen, ...) tritt überall dort auf, wo die lokale Fluenz eine
Materialschwelle F_th überschreitet. Der Rand der beschädigten Fläche liegt
also bei genau der Stelle r₀, an der F(r₀) = F_th gilt. Löst man das nach r₀²
auf, ergibt sich

```
r₀² = (w₀² / 2) · ln(F₀ / F_th)
```

**Das ist exakt der Wert, den die Haupttabelle unter „r₀²" zeigt.** Die
Segmentierung liefert pro Spot eine Fläche A (die Pixelfläche der Kontur);
unter der Annahme eines kreisförmigen Schadensbereichs gilt A = π·r₀², die
Tabelle rechnet also nur zwischen A und r₀² = A/π um - beide stecken die
gleiche Information. (In der klassischen Formulierung von Liu wird
stattdessen mit dem Durchmesser D = 2·r₀ gerechnet, D² = 4·r₀² - inhaltlich
identisch, nur anders skaliert.)

Da die Spitzenfluenz F₀ proportional zur Pulsenergie E ist
(F₀ = 2E / (π·w₀²), Energie geteilt durch die effektive Strahlfläche),
lässt sich das umschreiben in eine **lineare Beziehung zwischen r₀² und
ln(E)**:

```
r₀² = (w₀² / 2) · ln(E) − (w₀² / 2) · ln(E_th)
        \_________/                \___________________/
           Steigung                     y-Achsenabschnitt
```

Genau diese Gerade fittet FluenceScan automatisch, sobald Konturen (für A)
und Energien (für E) vorliegen (siehe [2.3](analyse-starten.md#23-ergebnis-liu-auswertung-tabelle-diagramm)):
r₀² wird gegen ln(E) aufgetragen, linear regressiert. Aus der **Steigung**
der Geraden folgt der Strahlradius w₀ (Steigung = w₀²/2), aus dem
**Achsenabschnitt** die Schwellenenergie E_th - und mit
F_th = 2·E_th / (π·w₀²) daraus die gesuchte Fluenzschwelle F_th, die im
Liu-Diagramm als Nullstelle der Geraden erscheint (dort, wo r₀² = 0 wird).

## A.2 Mehrpuls-Inkubation nach Jee, Becker & Walser (1988)

Trifft nicht ein einzelner Puls, sondern eine Folge von N Pulsen auf
dieselbe Stelle, sinkt die effektive Zerstörschwelle mit jedem weiteren
Puls messbar ab - die Oberfläche "erinnert sich" an vorangegangene,
unterschwellige Belastung. Diesen Effekt nennt man Inkubation. Das
Mehrpuls-Modell beschreibt ihn als

```
F_th(N) = F_th(1) · N^(S−1)
```

mit dem Inkubationskoeffizienten S (0 < S ≤ 1). Bei S = 1 gibt es keine
Inkubation (F_th(N) = F_th(1), unabhängig von N); je kleiner S, desto
stärker sinkt die Schwelle mit zunehmender Pulszahl. Zur Einordnung: Bei
S = 0,8 liegt die Schwelle nach N = 10 Pulsen bei F_th(10) = F_th(1) · 10^(-0,2)
≈ 0,63 · F_th(1) - nach zehn Pulsen reicht also nur noch gut 60 % der
Einzelpuls-Fluenz, um das Material zu verändern.

`N_Pulses` und `S` in der Meta-Tabelle sind genau diese beiden Größen:
`N_Pulses` (die Anzahl der Pulse, mit der der jeweilige Spot bestrahlt
wurde) ist meist bekannt, während sich `S` nicht aus einer einzelnen
Liu-Auswertung bestimmen lässt - es braucht wiederholte Messungen bei
verschiedenen N (z. B. je eine Serie mit N = 1, 10, 100 Pulsen), aus denen
sich F_th(N) für jedes N per Liu-Fit ergibt; die Steigung von log(F_th(N))
gegen log(N) liefert dann S − 1. FluenceScan führt diesen Mehr-N-Fit selbst
nicht durch - `S` wird als bekannter, extern bestimmter Wert (aus der
Literatur oder einer eigenen Messreihe) eingetragen, um daraus die
Einzelpuls-Schwelle F_th(1) für den aktuell geladenen Stapel zu berechnen.

Quelle: Jee, Y., Becker, M. F., & Walser, R. M. (1988). *Laser-induced
damage on single-crystal metal surfaces.* JOSA B, 5(3), 648-659.
[doi.org/10.1364/JOSAB.5.000648](https://doi.org/10.1364/JOSAB.5.000648)

## A.3 GLG-Aperturkorrektur (García-Lechuga & Grojo, 2021)

Die Herleitung in [A.1](#a1-die-d2-methode-nach-liu-1982) setzt ein ideales
Gauß-Profil voraus. Reale Laserstrahlen weichen davon ab - insbesondere,
wenn eine Kreisblende zur Strahlformung im Aufbau sitzt (üblich, um ein
unsauberes Rohprofil zu bereinigen), entsteht statt eines reinen
Gauß-Profils ein beugungsbeeinflusstes Profil, das mit wachsender
Abschattung durch die Blende zunehmend einer Airy-Scheibe ähnelt statt
einer Gauß-Glocke. Wird die Liu-Auswertung trotzdem mit den unveränderten
Gauß-Formeln aus A.1 gerechnet, ergibt das - je nach Stärke der
Blenden-Abschattung - einen systematischen Fehler der Fluenzschwelle von
teils über 20 %.

Die eigentliche **lineare Regression bleibt unverändert**: r₀² wird wie in
A.1 gegen ln(E) aufgetragen und gefittet, die Steigung liefert w₀ weiterhin
fast unverändert. Was sich ändert, ist die **Interpretation** der daraus
berechneten Fluenzwerte - García-Lechuga & Grojo führen dafür zwei
multiplikative Korrekturfaktoren η_F und η_Eth ein:

```
F₀      = (2·E)     / (π·w₀,Liu²) · η_F
F_th    = (2·E_th,Liu) / (π·w₀,Liu²) · η_Eth · η_F
```

η_F und η_Eth sind tabellierte Werte (im Paper als Tabellen angegeben), die
von zwei Größen abhängen: der Aperturtransmission PT und dem
Energiebereich, der für den Fit verwendet wurde (ausgedrückt als Vielfaches
von E_th, z. B. bis 2·E_th). Bei PT = 75 % und einem Fit bis 2·E_th liegen
sie beispielsweise bei η_F ≈ 1,033 und η_Eth ≈ 1,006 - die Korrektur ist
also klein, aber systematisch, und wächst mit stärkerer Abschattung
(kleinerem PT).

Entscheidend als Eingabe ist damit die **Transmission der Kreisblende in
Fokalposition (PT)**: der Anteil der eingestrahlten Leistung, der die
Blende passiert und tatsächlich auf der Probe ankommt. Sie lässt sich
direkt messen - Laserleistung vor und nach der Blende erfassen und
dividieren, PT = P_nach / P_vor - ganz ohne zusätzliche Strahldiagnostik
wie eine Kamera am Fokus. Ist PT bekannt, zieht FluenceScan die
entsprechend korrigierte Gerade (näherungsweise parallel zum
ursprünglichen Liu-Fit) in Tabelle und Diagramm nach.

Quelle: García-Lechuga, M., & Grojo, D. (2021). *Simple and robust method
for determination of laser fluence thresholds for material modifications:
an extension of Liu's approach to imperfect beams.* Open Research Europe,
1, 7.
[doi.org/10.12688/openreseurope.13073.2](https://doi.org/10.12688/openreseurope.13073.2)

## A.4 Mittelung gleicher Energien im Array-Modus

Im Array-Modus (siehe [3.1](zusatzfunktionen.md#31-proben-anordnung-sample-layout))
wird angenommen, dass mehrere Spots mit derselben Energie bestrahlt wurden.
FluenceScan mittelt dazu sowohl die Pulsenergien aller Spots eines
Energielevels als auch die resultierenden Flächen dieser Spots zu je einem
gemittelten Energie- und Flächenwert. Erst mit diesen gemittelten Werten -
einem Wertepaar pro Energielevel statt einem pro Einzelspot - läuft die
Liu-Auswertung aus [A.1](#a1-die-d2-methode-nach-liu-1982), da diese von
genau einem D²/r₀²-Wert je Energie ausgeht.
