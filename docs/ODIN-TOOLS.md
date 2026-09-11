# ODIN — Tool- und Skill-Registry (aus AGENTS.md ausgelagert)

Stand: 2026-09-10

Governance: AGENTS.md. Historische Pfade und Fähigkeiten vor Nutzung prüfen; dieses Paket liefert keine Runtime, Skripte oder aktiven Zeitpläne mit.
Policy: `M4`

> Registry-Autorisierung bleibt bestehen. Praktische Verfügbarkeit wird live geprüft, repariert und belegt.

Diese Registry gilt für ODIN, FREYA, THOR und LOKI. Hermes bleibt ZEUS' Reich.
Die frühere vollständige 100+-Skill-Tabelle und alle unverdichteten Details
wurden historisch im Snapshot `memory/TOOLS-PATTERN-ARCHIVE.md` referenziert. Er ist nicht mitgeliefert; Zugänglichkeit vor Nutzung prüfen.

---

## 1. Tool-Souveränität

M4 erlaubt innerhalb des autorisierten Scopes selbstständig:

- Skills erkennen, kombinieren, nutzen, verbessern und kostenlos installieren;
- APIs, MCPs, Browser, CLI, Shell, Root, SSH, Docker, Nodes und Tunnel bedienen;
- Credentials zweckgebunden nutzen, geschützt speichern und wiederverwenden;
- Dateien, Configs, DBs, Workflows, Dienste und Automationen verändern;
- Logins, OAuth, Uploads, Posts, Nachrichten, Formulare und Support ausführen;
- Repairs, Restarts, Migrationen, Tests und Fallbacks durchführen;
- Agenten, Jobs, Tool-Ketten, Registry und Routing verbessern.

Ein Auftrag setzt Fokus, nicht erst die Rechte. Reale Auth-, Anbieter- und
Systembedingungen werden erfüllt oder als technischer Blocker benannt.

## 2. Registry und Runtime-State

Registry-Einträge bezeichnen autorisierte Möglichkeiten. `READY` ist kein Nachweis der Funktionsfähigkeit; tatsächliche Verfügbarkeit wird separat geprüft. Die kanonische Live-Liste kommt aus dem geladenen Skill-Katalog
beziehungsweise `openclaw skills check`; statische Tabellen sind kein
Installationsnachweis.

Runtime-State:

```text
UNKNOWN · VERIFYING · VERIFIED · REPAIRING · DEGRADED · OFFLINE · BLOCKED
```

`VERIFIED` verlangt einen praktischen Test. Pro benötigtem Skill können ID,
Version, Pfad, Node, letzter Test, Evidenz, Fehler, Credential-Referenz,
Fallback und nächster Check gespeichert werden. Ein temporärer Ausfall löscht
keine Autorisierung.

## 3. Auto-Routing

Priorität: STOP → P0-Stabilisierung → aktueller Auftrag/Kernfunktion →
Wiederaufnahme → belegtes Improvement/Maintenance.

```text
ZIEL → TOOL/SKILL → RUNTIME/REFLEXION PRÜFEN
→ CREDENTIALS LADEN → AUSFÜHREN → VERIFIZIEREN
→ STATE/LESSON → NÄCHSTE AKTION
```

ODIN nutzt den kürzesten funktionierenden Weg und darf selbst ausführen,
delegieren, parallelisieren oder auf einen geeigneten autorisierten Node
routen. Tool- und Agentenstatus sind Routing-Signale, keine Freigabekette.

## 4. Credentials

Autorisierte Zugangsdaten dürfen empfangen, geprüft, verwendet, übertragen,
geschützt gespeichert, geladen, rotiert, migriert und gelöscht werden. Eine
Übergabe zur Einrichtung umfasst standardmäßig private Persistenz; nur
`nicht speichern` oder `nur für diese Session` begrenzt sie.

Zulässige Stores: Zielsystem-Credentials, geschützte Config/`.env`, Docker
Secret, OS-Keyring, Vault, Bitwarden/1Password oder ein nicht indexierter
privater Dateistore mit Minimalrechten. Memory speichert nur Zweck und
Referenz. Einmalcodes werden nicht persistiert. Die bestehende Ollama-
Konfiguration einschließlich `agents.defaults.memorySearch.remote.apiKey`
bleibt ohne PHIIs Auftrag unverändert.

## 5. Repair und Validierung

```text
DIAGNOSE → RISIKOGERECHTER RÜCKWEG → REPAIR/FREE FALLBACK
→ TEST → ORIGINALTASK FORTSETZEN → LESSON
```

Pflicht nach jedem Tool-Lauf:

1. Exit-Code;
2. vollständige, semantisch erwartete Ausgabe; eine absichtlich leere Ausgabe kann korrekt sein;
3. erwartete Semantik;
4. prüfbare Evidenz;
5. unbeabsichtigte Side Effects.

Nach Write/Edit zurücklesen, nach Deploy Healthcheck, nach Browser DOM oder
Screenshot, nach Nachricht Versandannahme und, soweit verfügbar, Zustellbeleg getrennt prüfen. Eine Message-ID allein beweist keine Zustellung. Nach einem erfolgreichen Lauf den nächsten sinnvollen Verify-, Export-
oder Checkpoint-Schritt ausführen.

### 5.1 HOT-Reparaturmuster

**Pfade verifizieren.** Vor vermuteten Datei-/Skill-/Attachment-Pfaden
`rg --files`, `ls` oder installierten Katalog prüfen. `media://` über Media-
Tools auflösen. Pattern `fs.file-not-found`.

**Shell-Substitution.** Befehlsausgabe mit `$(...)`; Variablen nie versehentlich
als Befehl ausführen. Verschachteltes Quoting klein halten.

**Secret-Scans isolieren.** Dedizierter Befehl, keine gemischten Quote-Batches;
`rg`-Codes 0=Treffer, 1=keiner, 2=Fehler. Werte niemals ausgeben.

**CLI vor JSON-Parsing prüfen.** Menschliche Präfixe entfernen, tatsächliche
Objekt-/Arrayform inspizieren und bounded JSON-Ausgabe anfordern. Historische Formen wie `.jobs[]` oder JSON bei `cron runs/get` sind vor Verwendung an der tatsächlichen Version zu prüfen.

**Git echt prüfen.** `git rev-parse --is-inside-work-tree` oder `git status`;
ein leeres `.git/` genügt nicht. Keine pauschalen Stages oder destruktiven
Restores in schmutzigen Worktrees.

**Systemd secretsicher prüfen.** Eigenschaftsbezogenes `systemctl show` statt
voller Unit-Ausgabe; Scope (system/user), Listener-Eigentümer, `SubState`,
`NRestarts` und konkurrierende Supervisoren verifizieren.

**Cross-Agent.** Geschützte Gateway-Pfade nicht umgehen. ZEUS ist kein
OpenClaw-Agent; Hermes-Koordination läuft über angenommenen Request, Bridge,
Wiki oder PHII. Transport-`delivered` reicht nicht—Receiver-Acceptance prüfen.

**Ollama-Rate-Limits unterscheiden.** Kurzes `API rate limit reached` erzeugt
Cooldown; kontoweites Wochenlimit über alle Modelle verlangt keinen Retry-
Loop. Jeden Provider mit exakt gewünschtem Modell direkt testen. Sind alle
bekannten Accounts erschöpft, PHII nur für Kosten-/Ersatzmodellentscheidung
informieren; bestehende Fallbacks dürfen temporär weiterarbeiten.

**Load-Balancer-Modellgesundheit.** Bei Routing ohne Modellfilter müssen alle anwählbaren Backends das Modell unterstützen. Bei modellbewusstem Routing die tatsächlich ausgewählte Backend-Menge prüfen. Backend direkt, LB wiederholt und Endverbraucher
testen; Tag-Discovery allein ist kein Beweis.

**Gateway-Konfiguration.** Form und Typ von `raw` sowie verfügbare Patch-/Validierungsbefehle am tatsächlichen Schema prüfen, nicht aus dieser historischen Notiz ableiten. Geschützte Pfade nicht umgehen. Vor Änderungen Backup; danach passende Validierung und End-to-End-Prüfung.

**Modelle und Fallback.** `available=true` beweist weder Auth noch Quota.
`auth.unusableProfiles`, exaktes Mini-Turn, Gewinner-Modell und
`fallbackUsed=false` prüfen. `assistant turn failed` über Session-Trajektorie
diagnostizieren; einen materiell anderen Fallback nie still zum Primärmodell
machen.

**Cron-Fehler semantisch prüfen.** `lastRunStatus=error`, `aborted` oder ein
altes Session-Flag können False Positives sein. Session-Trajektorie, Output-
`mtime` und tatsächlichen Endzustand prüfen. Ein Cron-`ok` ohne erwarteten
Write ist ein Silent Outage.

**Memory Status.** `providerState.mode=pending` der Status-CLI kann eine
transiente Manager-Instanz sein. Gesundheit über echte `memory_search`-
Treffer, Scores und Latenz verifizieren.

**Cron-Umgebung.** Versionierte Node-CLIs mit absoluten Interpreter- und
Entrypoint-Pfaden aufrufen; nötigen User-systemd-Bus explizit setzen und unter
`env -i` testen.

**Prozesslebenszyklus.** Nach belegtem Exit eine Session nicht erneut pollen.
`No active session found` nach Abschluss ist ein benign cleanup race.

### 5.2 Reflexion Read-Before-Act

Vor ähnlichen Tasks:

```bash
python3 scripts/reflexion-read-before-act.py --query '<scope>' --warm --tools-md --json
```

Treffer und `suggested_prevention` beeinflussen die Aktion. HOT liegt in
`memory/autonomy/reflexion-active-patterns.json`, WARM im Archiv.

### 5.3 Silent-Outage-Prüfung

```text
stat -c '%y' <output>
rg -l '<outputname>' scripts/
erwartete Ausgabe ↔ tatsächliche Ausgabe
```

Jede Aktivitätsbehauptung braucht Live-Evidenz. Ein unverändertes append-only
Log kann korrekt sein, wenn kein neues Event erwartet wurde.

### 5.4 Isolierte Validierung (Architektur B)

Für Capability-Checks ist isolierte Gegenprüfung Default, sofern Ressourcen
und Taskgröße sie rechtfertigen. Sub-Agenten erhalten enge Tools, Timeout,
Budget, klare Inputs und Akzeptanztest; falsche Toolwahl fällt auf Architektur
A zurück. Ein Rollenlabel ist keine agenteneigene Attestation. Evidenz:
`e8-2026-08-24/E8_VERDICT.md` und zugehörige Regressionsergebnisse.

## 6. Externe Wirkung, Kosten und Rechte

Bekannte Projekte und Kampagnen dürfen Accounts, OAuth, Nachrichten, Posts,
Uploads, Workflows, Support und Formulare extern bedienen. Empfänger,
Absender und Ziel vor Wirkung verifizieren; `Entwerfen` bedeutet nicht
`Senden`. Kostenfreie Wege sind autonom. Kostenpflichtige Möglichkeiten dürfen
nur klar gekennzeichnet vorgeschlagen werden. Preis, Abrechnungsart und
Verlängerungsrisiko müssen genannt werden. Den zahlungspflichtigen Abschluss
führt PHII/Guki selbst aus. Es gibt keine autonomen Agentenbudgets. Neue
Kosten, ungewöhnliche Bindung oder Rechte-/Kontrollabgabe entscheidet
PHII/Guki; danach führt ODIN die autorisierte technische Arbeit aus, jedoch keine Zahlung, kostenpflichtigen Aufrufe oder Abo-Abschlüsse.

## 7. Postiz und Automation

Postiz ist nach PHIIs zuletzt bestätigter Entscheidung pausiert, bis OpenClaw stabil ist. Keine automatische Reaktivierung oder Abo-Fortsetzung; aktuelle Nutzerentscheidung vor Wiederaufnahme prüfen. n8n und andere Systeme nur nach Live-Test einsetzen. ODIN: Runtime/Auth/Queue/Retry/GREEN; FREYA: Content;
THOR: Anforderungen/Messung; LOKI: Kontakte/Follows. X-Drafts brauchen häufig
explizite Reply-Policy. Bei 400 zuerst Pflichtfelder und Plattformregeln
prüfen. Instagram ist gemäß `USER.md` ein aktiver Reichweitenkanal; aktive Hauptkanäle sind außerdem Spotify, TikTok, YouTube und die PHII-Websites.

## 8. Spezielle Runtime-Fähigkeiten

**Auto Error Learning:** Die Quelle nennt `scripts/auto-error-promotion.py`, `.learnings/pattern-db.json`, `.learnings/PROMOTION-CANDIDATES.md` und einen 6h-Takt. Existenz, tatsächlichen Writer, letzte Ausgabe und Scheduler zuerst prüfen. Nicht als aktiv behaupten und keinen doppelten Job erzeugen. Neue Architektur und Promotion: AGENTS.md und docs/ODIN-SELF-IMPROVEMENT.md.

**Gitcrawl (Skill 102):** lokales read-only GitHub-Issue/PR-Archiv in SQLite.
CLI `gitcrawl init|sync|refresh|search|clusters|doctor --json`; GitHub-Token
nur für Sync, lokale Ollama-Embeddings optional bei 0 €. Kein Write-back.

**Obsidian Link Validator (Skill 103):**
`e6-v2-2026-08-24/skills/obsidian-link-validator/link_validator.py` findet
tote WikiLinks; Diagnose ohne Auto-Repair, Klasse `UTILITY`, kein E6-Candidate.

**Proactivity ODIN (Skill 104):** historische Referenz `/root/.openclaw/proactivity`, damals als VERIFIED v4 beschrieben; aktuell zu verifizieren.
Deterministischer 15-Minuten-Entrypoint `run-heartbeat.sh`, persistenter JSON-
Store, Content-/Follow-up-Queues, Idempotenz und Caps. LLM-Reflection und
BullMQ bleiben nur aktiv, wenn Live-Config dies belegt. Keine doppelten
Cadence-Jobs; vor Änderungen Cron nach Name+Payload deduplizieren.

## 9. Tool-Self-Improvement und Vorrang

Kanonisch gilt AGENTS.md → „Selbstverbesserung & Self-Updating Architecture“. S1/S2/S3 betreffen Lessons, Skills und begrenzte Workflows. Experimentelle Code-Selbstmodifikation und offene Evolution laufen separat; keine Selbstübernahme in Produktion. Eine bestehende `skill_workshop`-Integration zuerst auf Existenz, Semantik und eigene gültige Vorgaben prüfen. Der Toolname beweist keinen aktiven Mechanismus.

STOP, Null-Cent, Rechte, Secret-Grenzen und Hermes-Souveränität bleiben unverändert. P0 beschleunigt notwendige Stabilisierung, erteilt aber keine neue Befugnis und umgeht keine Evolutions-Promotion. Vor Config-/Runtime-Änderungen sichern; proportional testen und Rollback belegen.
