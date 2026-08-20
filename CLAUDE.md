# Projektregeln für Claude

Diese Datei enthält verbindliche Arbeitsanweisungen für Claude in diesem
Repository. Sie ergänzt README.md (Nutzer-Doku, Englisch), richtet sich
aber ausschließlich an den Entwicklungsprozess. Geplante Arbeit wird über
GitHub Issues getrackt (Milestones bündeln zusammengehörige Batches),
nicht mehr über eine ROADMAP.md-Datei im Repo.

## Was dieses Repo ist

Eine ESPHome-Konfiguration nebst Doku, Fritzing-Schaltplan und Fotos für
den Umbau eines Tischfernsprechers W 48 zu einem Home-Assistant-Voice-
Assistant. Es gibt keinen kompilierten Code und keine HACS-Integration –
das Herzstück ist die YAML-Datei im Repo-Root.

## Workflow

- Code-Änderungen nicht direkt auf `main` committen. Für jede
  nichttriviale Änderung einen neuen Branch erstellen
  (`git checkout -b <kurzer-branch-name>`) und einen Pull Request öffnen.
- Commit-Messages beschreiben das "Warum", nicht nur das "Was".
- Die `version` unter `esphome: project:` in der YAML-Konfiguration nur
  bei tatsächlichen Konfigurationsänderungen hochzählen (Patch-Version,
  z. B. 0.2.3 → 0.2.4) – nicht bei reinen README-/Doku-Änderungen. Dieser
  Wert erscheint in Home Assistant als `sw_version` des Geräts und ist
  damit die einzige von außen sichtbare Versionsangabe des Projekts.
- Größere Refactorings (z. B. Architektur-Umbauten) vorher als Plan
  vorstellen und explizit bestätigen lassen, bevor der Code angefasst
  wird.

## Änderungen an der ESPHome-Konfiguration

- Jede Änderung an der YAML muss vor dem Öffnen eines Pull Requests
  mindestens `esphome config <datei>.yaml` gegen die aktuelle
  ESPHome-Version bestehen. Das Ergebnis im PR dokumentieren.
- `esphome config` prüft nur die Konfiguration, nicht das Verhalten auf
  echter Hardware. Änderungen an Audio-Pipeline, GPIO-Belegung oder
  Voice-Assistant-Ablauf sind erst nach einem Test am realen Gerät als
  erledigt zu betrachten. Ungetestete Änderungen im PR ausdrücklich als
  ungetestet kennzeichnen.
- `substitutions: name:` nicht ändern. Der Node-Name bestimmt die
  Entity-IDs in Home Assistant; eine Änderung bricht bestehende
  Installationen und Automationen.
- Breaking Changes von ESPHome immer am offiziellen Changelog und am
  Quelltext der betroffenen Komponente verifizieren, nicht aus dem
  Gedächtnis beantworten.

## Transparenz bei automatisiert erstellten Beiträgen

Jede von Claude erstellte Issue, jeder Pull Request und jeder Kommentar
in diesem Repository wird als solcher gekennzeichnet. Am Ende des Textes
steht dafür:

```
Assisted by: Claude:<aktuell genutztes Modell>
```

also z. B. `Assisted by: Claude:claude-opus-5`. Die Angabe ist Pflicht,
auch bei kurzen Kommentaren, und nennt das tatsächlich verwendete Modell.

## Umgang mit externen Pull Requests (STRIKT EINHALTEN)

Bevor an einer Issue gearbeitet wird, muss geprüft werden, ob dazu
bereits ein Pull Request von einem Contributor vorliegt (`gh pr list`,
auch auf Verweise zur Issue-Nummer in Titel/Body prüfen). Das gilt vor
jedem Arbeitsbeginn an einer Issue, nicht nur einmalig zu Sessionbeginn.

Trifft ein Pull Request von einem Contributor ein – zu einer bereits
gelösten Issue, oder inhaltlich nicht zu den Zielen des Projekts
passend –, wird er nicht stillschweigend ignoriert oder übernommen,
sondern beantwortet:

- Klarstellen, dass die Antwort von Claude Code stammt.
- Höflich ablehnen.
- Einen kurzen, fachlichen Grund für die Ablehnung nennen.

Ist der Pull Request inhaltlich gut, wird er dem Nutzer vorgeschlagen –
nicht eigenständig gemergt. Pull Requests von Dritten (nicht von Claude
selbst erstellt) benötigen vor dem Merge immer die ausdrückliche
Freigabe des Nutzers, ohne Ausnahme.

## Release-Regel (STRIKT EINHALTEN)

Sobald ein Befehl zur Erstellung eines Releases oder Git-Tags erteilt
wird, MUSS Claude den Nutzer zuerst explizit fragen:

> „Soll dieses Release als Beta-Version (Pre-release z. B. v1.0.0-beta.1)
> für HACS-Tester oder als finale Standard-Release (z. B. v1.0.0)
> veröffentlicht werden?"

Kein Release/Tag wird erstellt, bevor diese Frage gestellt und eindeutig
beantwortet wurde – unabhängig davon, wie der ursprüngliche Befehl
formuliert war.
