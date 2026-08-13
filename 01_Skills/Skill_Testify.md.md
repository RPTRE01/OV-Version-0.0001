# Skill: Testify / System-Validator (V1)

## 1. Kurze Anweisung
Simuliere den angeforderten Ablauf unter Einbeziehung aller relevanten Dateien und erstelle einen ultrakurzen Testbericht.

## 2. Ziel
Sicherstellung der Systemintegrität und Fehlerfreiheit durch gezielte Funktionsprüfungen bei minimalem Token-Verbrauch.

## 3. Controlparameter
* **Token-Schutz:** Jedes Testverfahren ist strikt auf maximal **3 Durchläufe** (Test-Runden) begrenzt. Nach Durchlauf 3 stoppt der Test automatisch.
* **Ablauf-Simulation:** Das Modell MUSS alle im Prozess erwähnten Dateien gedanklich laden und den logischen Datenfluss Schritt für Schritt simulieren.
* **Gezielter Testbericht:** Das Ergebnis MUSS in einem kurz gefassten Bericht mit exakt 4 Kernpunkten ausgegeben werden:
  1. *Status:* (Bestanden / Fehlgeschlagen)
  2. *Fehleranalyse:* Kurzer Hinweis auf Fehler oder logische Haken, die das Ergebnis verfälschen.
  3. *Prozess-Hindernisse:* Probleme, die während des Ablaufes aufgetreten sind.
  4. *Verbesserungen:* Maximal 3 präzise Vorschläge zur Optimierung.

## 4. Abbruchbedingung
* **Runden-Limit:** Sobald der 3. Simulationsdurchlauf beendet ist, bricht der Skill ab und erzwingt die Ausgabe des Abschlussberichts.
* **Kompaktheits-Verletzung:** Schwenkt das Modell in lange Fließtexte oder Erklärungen ab, wird die Simulation sofort gestoppt.
* **Zirkuläre Referenz (Loop-Stopp & Log-Zwang):** Sobald sich zwei oder mehr geladene Unterdateien gegenseitig im Kreis referenzieren oder ein Prozessschritt blockiert, MUSS die Simulation augenblicklich abgebrochen werden. Der Test gilt als "Fehlgeschlagen". * *Log-Zwang:* Die KI MUSS im Bericht unter "Fehleranalyse" zwingend ein präzises Log-Protokoll ausgeben: **`[Fehler: Zirkelschluss] -> Betroffene Dateien: [Datei_A.md] & [Datei_B.md] -> Verursachende Befehlszeile/Regel: [Exakter Text der Zeile]`**.