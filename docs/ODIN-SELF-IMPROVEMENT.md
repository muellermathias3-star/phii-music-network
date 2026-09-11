# ODIN — Self-Improvement und kontrollierte Evolution
Stand: 2026-09-10
Status: Betriebsentwurf in Core-Dateien; keine implementierte Evolutionsruntime

Kanonische Autorität und Promotion: AGENTS.md. Dieses Dokument erläutert Umsetzung und Prüfung. Bestehende S1–S5-Begriffe sind hier eine lokale Einteilung, keine verbindliche Taxonomie der zitierten Forschung oder von OpenClaw.

## Drei Arbeitsarten
| Art | Beispiel | Ausführung |
|---|---|---|
| Normale M4-Arbeit | Beauftragte Entwicklung, konkrete Gateway-Reparatur, Integration einrichten | Im autorisierten Reich; Config/Runtime vorher sichern, proportional prüfen |
| S1–S3-Verbesserung | Lesson, geprüfter Skill, bessere Prompt-/Routingfolge | Im tatsächlichen Workspace; dokumentierte Evidenz und kanonische Promotion |
| S4/S5-Experiment | Eigenen Agentencode mutieren, Varianten erzeugen und anhand Aufgaben auswählen | In technisch isolierter Experimentumgebung; eigene Live-Promotion nach PHII-Bestätigung |

Die Einordnung folgt tatsächlicher Wirkung, nicht Dateiendung oder Label. Ein experimenteller Code-Selbstumbau wird nicht durch Umbenennung in „Prompt-Optimierung“ zur Routine-Reparatur.

## Lessons-Dateien und Datenfluss
Relative `.learnings/`-Pfade beziehen sich auf den verifizierten ODIN-Workspace. Vorhandene Mechanik und Formate prüfen und weiterverwenden. Keine parallele Pattern-Datenbank allein aufgrund dieses Entwurfs erzeugen.

| Ziel | Inhalt |
|---|---|
| .learnings/ERRORS.md | Fehler, Ursache/Hypothese, Pattern-Key, Evidence und konkrete Prävention |
| .learnings/LEARNINGS.md | Verifizierte Recoveries und hilfreiche Muster mit Geltungsbereich |
| .learnings/FEATURE_REQUESTS.md | Fehlende Fähigkeit, konkreter Bedarf, kostenlose Prüfmöglichkeit |
| WARM | Unbestätigte oder noch nicht ausreichend wiederholte Kandidaten |
| HOT | Kuratierte tatsächlich gültige Regeln/Referenzen |
| COLD | Historische, abgelöste oder selten benötigte Details mit Status |

Ein gemeinsamer Pattern-Key verbindet Fallbelege. Zähler erfassen unabhängige bestätigte Einsätze, nicht wiederholte Verarbeitung desselben Logs. Eine neue Fehlerursache oder ein Gegenbeleg muss die bisherige Lesson begrenzen können.

Lesson-Vorlage:

```markdown
### <Pattern-Key> — <kurzer Titel>
- Status: WARM / bestätigt / abgelöst
- Datum und Scope:
- Ziel und Aktion:
- Resultat und Side Effects:
- Evidenzreferenz und Prüfzeitpunkt:
- Positives / Negatives:
- Ursache: belegt oder Hypothese
- Unabhängige bestätigte Fälle:
- Gegenbelege / Gültigkeitsgrenzen:
- Nächstes Verhalten:
- Promotion: Ziel, Begründung, erforderliche Bestätigung
- Speicherziel und abgelöster Eintrag:
```

Rohlogs und Secrets bleiben draußen. In MEMORY.md nur kurze bestätigte Erkenntnisse und Referenzen, keine zweite Kopie aller Lessons. Neue technische Tatsachen oder direkte PHII-Korrekturen werden nicht wegen einer Drei-Fälle-Regel blockiert; diese gilt für die Verallgemeinerung eines Musters.

## Umsetzung des Schedulers
Die Quelle nennt auto-error-promotion.py alle 6h, ein Review um 04:00 UTC und Skill 104 mit 15-Minuten-Takt. Diese sind historische Angaben, keine neu eingerichteten Jobs.

Vor Einrichtung prüfen: vorhandener Job, Owner, Payload, reales Skript, letzter erfolgreicher Lauf, Ausgabedatum, Fehlerpfad, Pause/STOP, Deduplizierung. Erst dann vorhandenen Ablauf anpassen oder fehlende Mechanik als eigene autorisierte Aufgabe implementieren. Ein Vermerk „alle 6h“ in Markdown startet nichts.

Der mitgelieferte Ambient-Heartbeat bleibt kurz und begrenzt. Ein Lessons-Review läuft in einer separaten geeigneten Task-/Automation-Session. BOOT darf begrenztes Lernen und gültiges Resume nach BOOTSTRAP.md bearbeiten; vorbereitete isolierte Experimente und längere Reviews brauchen nachgewiesene dauerhafte Übergabe. Keine experimentelle Live-Promotion und keine Änderung von BOOT/BOOTSTRAP im Boot-Lauf.

## Evolutions-Workspace
Beispielstruktur, erst nach Prüfung des tatsächlichen Pfads einrichten:

```text
odin-evolve/
  manifest.yaml
  prompts/system.md
  skills/
  memory/
  candidates/
  evidence/
  .git/
```

Getrennte Bewertungsdaten und unveränderliche Test-/Gate-Steuerung müssen außerhalb des vom Kandidaten beschreibbaren Bereichs liegen. Ein Git-Worktree auf demselben Host ist Versionsisolation, keine Zugriffssperre.

Manifest-Felder für die spätere Implementierung (lokales Sollformat, kein OpenClaw-Config-Schema):
- experiment_id, owner, baseline_commit, candidate_commit;
- tatsächlicher Workspace, Isolation und überprüfte Mounts/Rechte;
- erlaubte Mutationspfade, unveränderliche Dateien und ausgeschlossene Produktionspfade;
- Modell und nachweislich kostenloser Ausführungsweg;
- Daten-/Testsatzversion, Entwicklungsaufgaben, Holdout-Referenz;
- Baseline, Zielmetrik, Regressionsgrenzen;
- maximale Iterationen, Laufzeit, CPU, RAM, Speicherbelegung und Tokenverbrauch;
- STOP-/Timeout-Verhalten, Evidence-Pfad und Rollback;
- Promotionstatus, PHII-Bestätigung und freigegebener exakter Commit.

Konkrete Ressourcengrenzen werden anhand aktueller VPS-Last gewählt; hier keine veralteten CPU-/RAM-Werte voraussetzen. Offene Cloud-/API-Kosten sind mit Null-Cent unvereinbar. Das Paket erteilt keine Startanweisung für Benchmarkläufe.

## Hypothese bis Rollback

`HYPOTHESE → BASELINE → ISOLIERTE ÄNDERUNG → VERGLEICHSTESTS → ADVERSARIAL-/REGRESSIONSTESTS → ABRUCHKRITERIEN → REVIEW → PROMOTION ODER ROLLBACK`

Abbruch bei schlechterer Baseline, Sicherheits-/Autoritäts-/Scope-Verletzung, nicht reproduzierbaren Ergebnissen, fehlender Evidenz, unklaren Nebenwirkungen, unverhältnismäßigem Tokenverbrauch, Kosten oder unerlaubter Änderung von Identität, STOP, M4, Credentials oder Realm-Souveränität. Kandidat stoppen, gesicherten Ausgangszustand wiederherstellen und Rückweg prüfen. P0 schafft keine experimentelle Produktionsfreigabe.

### Isolierte innere Schleife: SOLVE → OBSERVE → MUTATE → GATE → RELOAD
1. Baseline an einer kleinen passenden Aufgabe messen, Ausgangscode und Umgebung versionieren.
2. Fehler und beobachtete Wirkung erfassen; keine angebliche Verbesserung aus Selbsteinschätzung ableiten.
3. Eine begrenzte Kandidatenänderung erzeugen; produktive Secrets, Accounts und Sendekanäle nicht verfügbar machen.
4. Syntax, Zielfunktion, kritische Regressionen und Ressourcenverbrauch prüfen; unter gleichen Bedingungen mit Baseline vergleichen.
5. Erfolgreichen Kandidaten nur im Experiment neu laden; Regression zum Snapshot zurückrollen.

Holdout-Aufgaben nicht als Optimierungstraining verwenden. Wenn Scores wiederholt zurückfließen, ist der Satz praktisch Teil der Entwicklung und darf nicht als unberührter finaler Holdout gelten. Vor finaler Promotion unabhängige frische Prüfung durchführen. Kandidat darf Tests und Bewertungslogik nicht zu seinen Gunsten ändern.

## Kostenlose erste Testideen
- Aus einem synthetischen Providerfehler einen korrekten Diagnosepfad ableiten, ohne echten Account-Aufruf.
- Ein kaputtes Wiki-Link-Beispiel erkennen; nur temporäre Testdateien verwenden.
- Zwei synthetische doppelte Queue-Aktionen erkennen, ohne Nachrichten zu senden.
- Aus einem bereinigten Incident-Text eine Lesson bilden und eine unbelegte Schlussfolgerung ausdrücklich markieren.

Das sind Vorschläge für spätere autorisierte Tests, keine ausgeführten Benchmarks. Keine fremden Erfolgswerte als ODIN-Leistung übernehmen.

## Live-Promotion
Vorlage für die konkrete Entscheidung:
- Baseline und exakter Kandidaten-Commit;
- reproduzierbarer Diff und getestete Zielumgebung;
- unabhängige wiederholte Verbesserungsbelege, Gegenbelege und kritische Regressionstests;
- Null-Cent, Scope, unveränderte PHII-/STOP-/Rechte-/Secret-Grenzen;
- Backup, Migrationsplan und praktisch geeigneter Rollback;
- PHIIs ausdrückliche Bestätigung für diesen Stand.

Nach Bestätigung erneut Version/Diff abgleichen, gezielt übernehmen und Produktionsfunktion prüfen. Der Evolutionsloop darf weder die Bestätigung selbst erzeugen noch seine Variante automatisch deployen. P0 führt zur notwendigen Stabilisierung im bestehenden Scope, nicht zum Überspringen dieser Promotion. Aktuelle beauftragte Reparaturen bleiben möglich.

## Quellen und Reichweite
- [A-Evolve](https://github.com/A-EVO-Lab/a-evolve): Referenz für agentische Evolutionsinfrastruktur; nicht als installiert übernommen.
- [Darwin Gödel Machine](https://sakana.ai/dgm/): Forschungsbeispiel für empirisch bewertete Änderungen am Agentencode.
- [Self-Improving Coding Agent](https://github.com/MaximeRobeyns/self_improving_coding_agent): Referenzprojekt zur Arbeit eines Coding-Agenten an der eigenen Codebasis.
- [Prime Agent](https://www.primeintellect.ai/blog/prime-agent): ergänzende Architekturquelle.

Der frühere Quellbericht bezeichnet diese Primärquellen als eingesehen; in dieser Korrekturrunde wurden sie nicht erneut geprüft. Die hier festgelegten Grenzen, Drei-Fälle-Regeln und manuellen Promotionsentscheidungen sind lokale Betriebsentscheidungen auf Grundlage des eingebrachten Vorschlags, keine durch diese Quellen vorgeschriebenen Standards. Der konkrete Nutzen für ODIN ist noch nicht gemessen.
