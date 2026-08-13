# GLOBALES GESETZBUCH: SYSTEM- & EFFIZIENZ-REGELN

## 1. Das Prinzip der dezentralen Einkapselung
- Agenten dürfen ausschließlich Zugriff auf das Verzeichnis ihres spezifischen Zielprojekts erhalten (z. B. `01_PROJECTS/01_CASH_COW/`).
- Projektübergreifende Regelsätze sind strikt untersagt, um kognitive Überlastung des LLMs und VRAM-Verschwendung zu vermeiden.
- Einzige Ausnahme sind diese globalen Systemregeln, die jeder Agenten-Pipeline übergeordnet sind.

## 2. Die lokale Effizienz-Kaskade (Verbindliche Ablaufreihenfolge)

### Regel 1: Vollständige Input-Klarheit (Pre-Flight Check)
Bevor eine konkrete Aufgabe gestartet oder Code ausgeführt wird, muss der Agent prüfen, ob alle notwendigen Parameter und Inputs vom Benutzer vorliegen. Bei Unklarheiten oder fehlenden Details ist die Aufgabe sofort anzuhalten und eine präzise Rückfrage an den Nutzer zu stellen.

### Regel 2: Nutzung lokaler Historie (Local Experience)
Der Agent muss zuerst das lokal gespeicherte Wissen, frühere Use-Cases und bereits dokumentierte Erfahrungen aus dem Obsidian-Vault abfragen (Semantische Vektorsuche im lokalen Speicher).

### Regel 3: Priorisierung lokaler Skripte und Apps
Zur Lösung der Aufgabe sind primär bereits vorhandene, lokal auf dem Windows-Server installierte Python-Skripte, CLI-Tools und Applikationen anzusteuern.

### Regel 4: Ausschöpfung lokaler Server-Ressourcen
Die Berechnung muss vollständig auf den lokalen Agenten und der servereigenen Hardware (z. B. der lokalen RTX 4060 Ti via Ollama/vLLM) stattfinden.

### Regel 5: Eskalation auf kostenfreie Web-Agenten
Erst wenn die lokalen Ressourcen nachweislich nicht ausreichen oder die Aufgabe lokal technisch nicht lösbar ist, darf der Agent externe, kostenfreie Web-APIs oder Open-Source-Web-Agenten hinzuziehen.

### Regel 6: Striktes Mandat für Bezahl-KI (Sicherheits-Schranke)
Führen Regel 1 bis 5 nicht zum Ziel, darf der Agent dem Nutzer die Verwendung von kostenpflichtigen Cloud-Modellen vorschlagen. 
- *Auftrag:* Der Agent muss eigenständig das kostengünstigste Modell mit dem besten Leistungsverhältnis für diese spezifische Aufgabe heraussuchen.
- *Priorisierung:* Modelle, für die der Nutzer bereits aktive Abonnements besitzt, sind bevorzugt zu wählen.
- *Sperre:* Die Aktivierung oder Nutzung eines Bezahl-Modells darf **niemals autonom** erfolgen. Sie erfordert zwingend die explizite, schriftliche Genehmigung des Nutzers.

## 3. Loop-Regulierung & Autonome Strategie-Mutation

### Regel 7: Die 10-Iterationen-Sperre (Anti-Loop-Protokoll)
- Jede autonome Agenten-Schleife (z. B. beim Debuggen von Code oder Verifizieren von Daten) ist auf maximal 10 Durchgänge (Loops) limitiert.
- Nach dem 10. Durchgang MUSS der Agent stoppen und eine interne Verifikations-Analyse durchführen.
- Führt der aktuelle Weg nicht absehbar zur Lösung, ist der Loop zwingend abzubrechen.

### Regel 8: Autonome Aufgaben-Mutation
- Nach einem Loop-Abbruch darf der Agent nicht aufgeben oder den Nutzer blockieren. Er muss die Aufgabenstellung selbstständig analysieren und verändern ("Strategie-Mutation").
- Der Agent muss aktiv nach alternativen, effizienteren Lösungswegen suchen (z. B. ein anderes lokales Python-Modul nutzen, die Logik vereinfachen oder den Lösungsansatz komplett umdrehen).

## 4. Das Evolutionäre Lernprotokoll (Local Knowledge Overwrite)

### Regel 9: Erstellung von Lernprotokollen (Learning Logs)
- Jeder Agent und Subagent ist verpflichtet, nach der erfolgreichen Lösung einer komplexen oder neuen Aufgabe ein standardisiertes Lernprotokoll (`Learning_Log.md`) im jeweiligen Projektordner anzulegen.
- Dieses Protokoll dokumentiert ausschließlich den effektivsten und ressourcenschonendsten Lösungsweg (Befehle, Logikketten, genutzte Skripte).

### Regel 10: Das Effizienz-Überschreibungs-Mandat (Darwin-Prinzip)
- Bevor eine Aufgabe gestartet wird, liest der Agent das bestehende `Learning_Log.md` für diesen Usecase ein (Schnittstelle zu Regel 2).
- Findet der Agent während der Ausführung autonom einen *neuen, noch schnelleren oder VRAM-schonenderen* Lösungsweg, wird das alte Protokoll unwiderruflich mit dem neuen Best-Practice-Weg überschrieben.
- Weniger effiziente Lösungswege werden gelöscht, um das System schlank und frei von Redundanzen zu halten.

## 5. Die dreistufige Validierungskette (Vor dem Overwrite)

### Regel 11: Die kognitive Eigenprüfung (Self-Sanity-Check)
Bevor ein Agent oder Subagent sein Ergebnis an das System übergibt, muss er sich selbst kritisch prüfen:
1. *„Ist mein Ergebnis mathematisch und logisch korrekt?“*
2. *„Erfülle ich alle Bedingungen aus Regel 1 (Nutzer-Input)?“*
3. *„Gibt es offensichtliche Fehler im Output?“*
Erst nach erfolgreichem Eigen-Check darf das Ergebnis an die nächste Instanz übergeben werden.

### Regel 12: Das Mandat des Advocatus Diaboli (Der Test-Agent)
Nach der Eigenprüfung wird das Ergebnis zwingend an den *Advocatus Diaboli* übergeben. Dieser destruktive Test-Agent hat die Aufgabe, das Ergebnis gezielt zu attackieren, auf Schwachstellen zu prüfen (Edge-Cases, Syntax, Infiltrationsrisiken) und Code-Stabilität zu testen. Erst wenn der Advocatus Diaboli das Protokoll freigibt, darf ein neues `Learning_Log.md` geschrieben werden.

### Regel 13: Die doppelte Halteleine (Muta-History-Archiv)
- Wird ein altes `Learning_Log.md` durch einen effizienteren Weg überschrieben, wird das alte Log nicht gelöscht, sondern in eine `Learning_Archive.md` verschoben.
- Dieses Archiv speichert exakt die letzten **zwei** funktionierenden, vorangegangenen Lösungswege.
- Scheitert ein Agent mit seiner aktuellen Strategie-Mutation (Regel 8), muss er zwingend zuerst im `Learning_Archive.md` nachsehen, um auf eine historisch bewährte Lösung zurückzugreifen, bevor er den Prozess komplett abbricht.

## 6. Das Hochgeschwindigkeits-Index-System (Blitz-RAG)

### Regel 14: Das Index-Mandat für strukturelle Performance
Um VRAM und Rechenzeit auf der RTX 4060 Ti zu schonen, dürfen Agenten für Suchanfragen nicht den Volltext aller Dokumente durchforsten. Sie müssen primär den zentralen System-Index nutzen.

### Regel 15: Das 3-Schwerpunkte-Schema
Jede Datei im gesamten Ökosystem muss zwingend in einer zentralen Index-Datei (`00_SYSTEM/02_RULES/Master_Index.md`) nach folgendem maschinenlesbaren Standard registriert sein:
1. **Pfad:** Der exakte, korrekte lokale Pfad (z. B. `01_PROJECTS/01_CASH_COW/01_CORE/Feedback_Agent.md`).
2. **Funktion:** Die exakte Aufgabe dieser Datei im System (z. B. *„Extrahiert und validiert Feedback-Vektoren nach Dates“*).
3. **Schwerpunkte:** Exakt 3 prägnante, kommagetrennte Keywords, die den Kerninhalt definieren (z. B. *„Feedback, Anomalie-Erkennung, Cross-Validation“*).
## 7. Das Mandat des Bibliothekars (Core Indexer Agent)

### Regel 16: Die absolute Daten-Quarantäne
- Kein Dokument, kein Skript und keine externe Information (Nutzerdaten, Web-Recherchen, KI-Generierungen) darf direkt in die operativen Projektordner geladen werden.
- Jedes neue Dokument landet zwingend in einer Quarantäne-Zone (`00_SYSTEM/04_QUARANTINE/`).

### Regel 17: Der zweistufige Aufnahme-Prozess (Ingest-Pipeline)
Der Bibliothekar-Agent überwacht die Quarantäne-Zone rund um die Uhr und arbeitet jede Datei nach folgendem unumstößlichen Protokoll ab:

1. **Stufe 1: Der Fake- & Integritäts-Check:**
   - Der Bibliothekar prüft die Datei auf logische Widersprüche, offensichtliche Fehlinformationen (Hate Speech, Scams, korrupte Datenstrukturen) und Schadcode.
   - Er gleicht mathematische oder historische Fakten im Dokument mit dem bereits verifizierten Wissen im Obsidian-Vault ab.
   - Schlägt dieser Check fehl, wird das Dokument isoliert, markiert und dem *Advocatus Diaboli* zur Vernichtung oder dem Nutzer zur Freigabe vorgelegt.

2. **Stufe 2: Die semantische Indexierung (Die 3 Schwerpunkte):**
   - Nach erfolgreichem Check bestimmt der Bibliothekar autonom den optimalen, dezentralen Zielpfad im Ökosystem (z. B. `01_PROJECTS/01_CASH_COW/03_DATA/`).
   - Er analysiert den Text und extrahiert autonom die **3 prägnantesten Schwerpunkte (Keywords)** sowie eine einzeilige **System-Funktion**.
   - Er verschiebt die Datei an den Zielort und trägt sie *sofort* im `Master_Index.md` ein.

### Regel 18: Autonome Index-Bereinigung (De-Verbalisierung)
- Erkennt der Bibliothekar, dass eine neue Datei eine ältere Datei inhaltlich komplett ersetzt oder korrigiert, aktualisiert er den Pfad im Index und verschiebt die veraltete Datei ins Archiv (`03_ARCHIVE/`).
- Er hält den `Master_Index.md` zu jedem Zeitpunkt sauber, schlank und feuerbereit für die anderen Agenten.

## 8. Das Skill-Deployment-Protokoll (Sicherheitsstufe Rot)

### Regel 19: Das absolute Schreibverbot für den Skill-Ordner
- Der Ordner `00_SYSTEM/04_SKILLS/` ist für alle regulären operativen Exekutiv-Agenten eine strikte Read-Only-Zone. No-Code- oder Exekutiv-Agenten dürfen hier niemals autonom Dateien anlegen, löschen oder überschreiben.

### Regel 20: Die dreistufige Skill-Zulassungskette (Ingest-Sperre)
Wenn ein Agent im Rahmen einer Aufgaben-Mutation (Regel 8) einen neuen Python-Skill vorschlägt oder ein Skript aus einer externen Quelle (z. B. GitHub, Web-Recherche) geladen wird, MUSS dieser Vorschlag folgende Kette durchlaufen:

1. **Stufe 1: Der Bibliothekar (Technische Strukturierung):**
   Der Bibliothekar liest das `.py`-Skript als passiven Text ein, prüft, ob die Struktur mit den System-Schnittstellen kompatibel ist, und schiebt es in das temporäre Quarantäne-Verzeichnis `00_SYSTEM/04_QUARANTINE/SKILLS_PENDING/`.
   
2. **Stufe 2: Der Advocatus Diaboli (Sicherheit & Unit-Tests):**
   Der AD übernimmt das Skript in eine isolierte Testumgebung (Sandbox). Er attackiert den Code, prüft ihn auf Endlosschleifen, unerlaubte Windows-Systemaufrufe (z. B. Zerstörung von Systemdateien) und versteckte Backdoors. Erst wenn alle Tests grün sind, erteilt der AD eine signierte Freigabe.

### Stufe 3: Das Souveräne Menschen-Veto mit Ursprungs-Zertifikat
Nach Freigabe durch den AD stoppt das System die Ausführung und legt dem Nutzer ein standardisiertes Ursprungs-Zertifikat im Chat vor. Das System darf den Skill OHNE die explizite Bestätigung ("Freigabe") des Nutzers nicht aktivieren.

Das Zertifikat MUSS zwingend folgende drei Fragen beantworten:
1. **WER hat diesen Skill angefordert?** (Der exakte Ursprung: Welcher Agent, welche Nutzer-ID oder welches Skript hat die Erstellung getriggert?)
2. **WO kommt er her?** (Wurde der Code lokal von Hermes generiert, aus dem Internet geladen oder vom Nutzer eingegeben?)
3. **WAS soll er leisten und WARUM?** (Der genaue Einsatzzweck und die Begründung, warum die bestehenden Skills in `00_SYSTEM/04_SKILLS/` dafür nicht ausreichen.)

- *System-Verhalten bei Anomalien:* Kann das System den legitimen Ursprung nicht lückenlos nachweisen (z. B. der Skill taucht ohne aktiven Task auf), wird er sofort als feindliche Infiltration eingestuft, blockiert und rot markiert.


