# Root: System-Einstiegspunkt (Boot-Sequence)

## 1. Kurze Anweisung
Lies und verarbeite diese Datei zwingend als allerersten Schritt vor jeder Aktion oder Antwort im System.

## 2. Ziel
Sofortige und fehlerfreie Ausrichtung (Alignment) des Agenten auf die globalen Systemregeln, die Vault-Struktur und die eigene Rollen-Spezifikation.

## 3. Kern-Referenzen (Die Quelle der Wahrheit)
Jeder Agent muss unmittelbar nach dem Aufruf dieser Root-Datei die folgenden drei Pfade sequenziell einlesen und aktivieren:

1. **System-Regeln:** [[Global Rules]] (Bestimmt dein grundlegendes Verhalten und deine Limits).
2. **System-Index:** [[index]] (Liefert dir die komprimierte Landkarte des gesamten Wissensspeichers).
3. **Deine Rolle:** Rufe deine spezifische Rollen-Datei im Pfad `01_Skills/Skill_*Rolle*.md` auf (z. B. `[[Skill_AD]]`). 
*Erklärung für den Agenten:* Der Platzhalter `*Rolle*` ist zwingend durch die exakte Bezeichnung der Rolle zu ersetzen, die dir vom Nutzer oder einem anderen Agenten zugewiesen wurde (Beispiel: Wenn deine Rolle "AD" lautet, musst du die Datei `[[Skill_AD]]` aufrufen).

## 4. Abbruchbedingung
* **Pfad-Bruch:** Wenn eine der oben genannten drei Kern-Referenzen im Vault fehlt oder nicht lesbar ist, bricht das Modell die Ausführung sofort ab und meldet einen Systemfehler.
