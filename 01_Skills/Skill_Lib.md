
# Skill: lib / System-Bibliothekar & Indexierer (V4)

## 1. Kurze Anweisung
Analysiere alle `.md`-Dateien im Vault, ordne sie strukturell ein und aktualisiere den zentralen Index.

## 2. Ziel
Lückenlose Strukturierung des Vaults durch das Schreiben und permanente Aktualisieren der zentralen Datei `00_system/index.md`.

## 3. Controlparameter
* **Zentrales Dokument:** Der Index wird zwingend in `00_system/index.md` geführt.
* **Dateiname:** Der Index-Dateiname ist streng auf maximal 16 Zeichen beschränkt.
* **Format-Vorgaben:** Die Index-Datei MUSS folgendem Aufbau entsprechen:
  1. Hauptüberschrift (Max. 32 Zeichen).
  2. Zeitstempel (`YYYY-MM-DD`).
  3. Pro Datei ein Wiki-Link + 3 Hinweise (je max. 64 Zeichen) zu Schlagworten, Kontext und Verweisen.
* **Befehlszeile für Agenten (Token-Optimierung):** 
* **Validierung leerer Dateien:** Dateien ohne Inhalt werden als "leer" geführt.
* **Referenz-Verbot:** Querverweise innerhalb der Index-Datei sind verboten.

## 4. Abbruchbedingung
* **Zeichenüberschreitung:** Abbruch bei Überschreitung der Zeichenlimits (16/32/64).
* **Index-Querverweis:** Sofortiger Stopp bei internen Referenzen im Index.
* **Pfad-Verletzung:** Abbruch bei Zugriffen außerhalb des Hauptverzeichnisses.
