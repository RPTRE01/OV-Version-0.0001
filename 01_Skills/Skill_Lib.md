
# Skill: System-Bibliothekar & Indexierer (V0.03)

## 1. Kurze Anweisung
Analysiere alle `.md`-Dateien im Vault, ordne sie strukturell ein und aktualisiere den zentralen Index.

## 2. Ziel
Lückenlose Strukturierung des Vaults durch das Schreiben und permanente Aktualisieren der zentralen Datei `00_System/index.md`.

## 3. Controlparameter
* **Zentrales Dokument:** Der Index wird zwingend in `00_System/index.md` geführt.
* **Dateiname:** Der Index-Dateiname ist streng auf maximal 16 Zeichen beschränkt.
* **Format-Vorgaben:** Die Index-Datei MUSS folgendem, komprimierten Aufbau entsprechen:
  1. Eine Hauptüberschrift (Maximal 32 Zeichen).
  2. Ein Zeitstempel der Aktualisierung (`YYYY-MM-DD`).
  3. Pro indexierter Datei ein Wiki-Link, gefolgt von exakt 3 kurzen Hinweisen (je max. 64 Zeichen):
     - Hinweis 1: Wesentliche Schlagworte (Keywords).
     - Hinweis 2: Wesentlicher Kontext des Inhalts.
     - Hinweis 3: Naheliegende Schlagworte oder verwandte Inhalte.
* **Validierung leerer Dateien:** Dateien ohne Inhalt werden im Index zwingend mit dem Status "Leer" gekennzeichnet.
* **Referenz-Verbot:** Interne Referenzen, Querverweise oder Verlinkungen untereinander sind *innerhalb* der Index-Datei strengstens verboten.

## 4. Abbruchbedingung
* **Zeichenüberschreitung:** Sobald ein Dateiname (16 Zeichen), eine Hauptüberschrift (32 Zeichen) oder ein Hinweis (64 Zeichen) das Limit überschreitet, bricht der Skill sofort ab.
* **Index-Querverweis:** Wenn versucht wird, Querverweise innerhalb des Index zu schreiben, stoppt die Ausführung.
* **Pfad-Verletzung:** Bei Zugriffen außerhalb des Hauptverzeichnisses erfolgt ein sofortiger Abbruch.
