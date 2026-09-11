# ODIN D1–D10 — Dokumentprüfung
Stand: 2026-09-11

Diese Korrektur erhält den korrigierten ODIN-Core und integriert die freigegebenen D1–D10. Grundlage: korrigiertes ODIN-ZIP; PR-Ausgangsstand 94668df695e8870d0579f86a6071931cadd1d873.

- Vollständige AGENTS, USER, MEMORY, SOUL, IDENTITY, HEARTBEAT, BOOT und BOOTSTRAP sowie beide ODIN-Betriebsdokumente.
- USER, SOUL und HEARTBEAT bytegleich zur korrigierten Grundlage; Avatar und konkrete HOT-Repair-Patterns erhalten.
- 28 statische Dokumentprüfungen am gelieferten Kandidaten bestanden. Kein Beleg für Runtime-Verhalten.
- Öffentliche MEMORY-Fassung ersetzt ausschließlich die konkrete Moltbook-Account-/Agent-ID durch einen privaten Store-Verweis. Die private Korrekturfassung bleibt erhalten.
- BOOT v5 ist eine gekennzeichnete Rekonstruktion aus vorhandenem BOOT v4 und freigegebenen Resume-Regeln; der frühere lokale v5-Volltext war nicht verfügbar.
- USER unter 4.000, alle Core-Einzeldateien unter 20.000 Zeichen. AGENTS: 19.979 Zeichen, nur 21 Zeichen Reserve. Künftige Mutationen erneut zählen.
- Die acht Core-Dateien überschreiten zusammen 60.000 Zeichen. Tatsächliches Inject-Set, Gesamtbudget und adapterspezifische Ladezeitpunkte: UNKNOWN. Keine pauschale Hot-Reload-Garantie.
- Startup, Resume, Subagentenidentität, echte Memory-Mutation, Secret-Redaction im Betrieb, Experiment-Abbruch und Rollback: UNVERIFIED. Keine VPS-Verbindung, Runtime-Änderung oder produktive Zustellung in dieser Prüfung.

Vor Deployment: tatsächlichen Workspace, Version, Agent-Zuordnung, Hook, Memory-Backend und Limits prüfen; betroffenen Bestand sichern; harmlose Tests in geeigneter Isolation ausführen. Dateien und Referenzen allein implementieren weder Runner noch Task-Store. HEARTBEAT nicht automatisch in bereits migrierten Monitor-Scratch zurückkopieren.

PR #12 bleibt zur Prüfung offen und wird nicht gemergt. Ein GitHub-Commit aktiviert diese Dateien nicht auf dem VPS.
