# GitHub Commit Flow

Repository: muellermathias3-star/phii-music-network. Öffentliche bereinigte Koordinationsschicht, kein privater Runtime-Workspace.

## Verbindlicher Ablauf
`git status → relevante Dateien prüfen → Diff prüfen → Secret-/Privatsphäre-Scan → Branch → Commit → Push Branch → Pull Request → Review → Merge erst nach Freigabe`

1. Repository, Branch und vorhandene Änderungen prüfen: `git rev-parse --is-inside-work-tree`, `git status --short`, `git diff`.
2. Relevante vollständige Dateien lesen; private Inhalte, Secrets, E2/E3, Rohlogs, Datenbanken und Memory-Exporte ausschließen. Scan nur Pfad/Zeile/Kategorie ausgeben lassen, keine gefundenen Vollwerte. Keine Treffer beweist keine allgemeine Geheimnisfreiheit.
3. Korrektur-Branch von erneut geprüfter Basis erstellen oder ausdrücklich bestätigten Branch verwenden. Bestehende Änderungen erhalten; keine destruktiven Restores und kein Force-Push als Routine.
4. Ausschließlich existierende, einzeln geprüfte Pfade stagen. BOOTSTRAP.md einschließen, wenn Teil des bestätigten Diffs. Keine pauschalen `git add .` oder Verzeichnis-Stages.
5. `git diff --cached` und `git status --short` erneut lesen; proportional prüfen. Commit mit konkreter Erklärung und GitHub-noreply-Adresse.
6. Nur den ausdrücklich bestätigten Branch pushen. Kein direkter Push nach main. PR erstellen/aktualisieren; Remote-Diff und Commit erneut lesen.
7. Review; Merge ausschließlich nach gesonderter Freigabe. Für PR #12 gilt derzeit: nicht mergen.

## Private Mutation und öffentliche Freigabe
Private Core-/Memory-Änderungen privat versionieren. Lokaler Audit-Commit autorisiert keine öffentliche Veröffentlichung. Öffentliche Fassung separat bereinigen und exakt prüfen. `.gitignore` ist kein Secret-Scan; bewusstes Allowlisting ersetzt keine Inhaltsprüfung.

Repo-Dateien gelten ohne belegte Workspace-/Deployment-Zuordnung nicht als aktive Core-Dateien. Ein Push installiert nichts auf dem VPS; ein erfolgreicher Markdown-Test beweist keine Runtime-Wirkung.
