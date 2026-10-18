# CRM Portfolio Demo

**Eine Projektpräsentation von [LeonScope](https://github.com/LeonScope)**
Full-Stack Developer · AI-Assisted Product Builder

[English](README.md) · [Fallstudie](docs/CASE-STUDY.de.md) · [Prüfergebnisse](docs/VERIFICATION.de.md)

Ein CRM für kleine Vertriebs- und Serviceteams: Kunden verwalten, Zuständigkeiten klären, Gespräche dokumentieren und nächste Termine planen. Dieses Repository zeigt das Projekt anhand von Screenshots, technischen Entscheidungen und dokumentierten lokalen Prüfungen. **Der Anwendungscode bleibt privat.**

![Übersicht mit erfundenen Kunden, Terminen und Aktivitäten](assets/dashboard-desktop.png)

## Was die Anwendung zeigt

- **Kundenablauf:** Kunden suchen, anlegen, bearbeiten und zuweisen; Notizen, Termine, Archiv und Wiederherstellung.
- **Zwei Rollen:** Administratoren verwalten den Kundenbestand. Mitarbeiter greifen nur auf ihre zugewiesenen, nicht archivierten Kunden zu. Der Server setzt diese Regeln durch.
- **Nachvollziehbare Änderungen:** Geschäftsvorgang und zugehöriger Verlaufseintrag werden gemeinsam gespeichert.
- **Geprüfter CSV-Import:** Upload → Prüfung und Vorschau → ausdrückliche Bestätigung. Ein ungültiger Import legt keine Kunden an.
- **Vorführbare lokale Demo:** deutsche Oberfläche, Desktop- und Smartphone-Ansichten, 40 erfundene Kunden und drei lokal erzeugte Konten.

## Ausgewählte Ansichten

| Importvorschau am Desktop | Fehlerprüfung auf dem Smartphone |
| --- | --- |
| [![CSV-Vorschau](assets/import-preview-desktop.png)](assets/import-preview-desktop.png) | <img src="assets/import-errors-mobile.png" width="220" alt="Mobile CSV-Vorschau mit ungültigen und doppelten Einträgen"> |

[Mobile Kundenliste](assets/customers-mobile.png)

## Technische Nachweise

**53 Anwendungstests · 430 Einzelprüfungen · 4 erfolgreiche Browserabläufe.** Diese Ergebnisse stammen aus einer frisch eingerichteten lokalen Kopie vom 18. Oktober 2026. Neuinstallation, wiederholte Einrichtung, PHP-Codeprüfung, Produktionsbuild und Abhängigkeitsprüfungen waren ebenfalls erfolgreich. Diese öffentliche Präsentation führt keine Anwendungstests auf GitHub aus und behauptet das auch nicht. [Prüfbericht und Grenzen](docs/VERIFICATION.de.md).

Die Anwendung verwendet **Laravel 13, PHP 8.4, Blade, SQLite und Vite**. PHPUnit prüft Fachregeln und Fehlerfälle; Playwright prüft vollständige Browserabläufe. Die [Fallstudie](docs/CASE-STUDY.de.md) erläutert die Entscheidungen und eine kurze Vorführung für ein Bewerbungsgespräch.

## Rolle und KI-Unterstützung

LeonScope legte das Portfolioziel fest, bestätigte die Produktrichtung und den Umfang und steuerte die Iterationen. Codex erzeugte Implementierung, Oberfläche, Beispieldaten und Tests und führte die dokumentierten Prüfungen aus. Die Unterstützung und die bei der Prüfung vorgenommenen Korrekturen sind offengelegt. Das CRM selbst ruft kein KI-Modell auf.

## Verfügbarkeit und Rechte

Dies ist eine Portfolio-Präsentation. Sie enthält weder den Anwendungscode noch ein Installationspaket, lokale Zugangsdaten oder eine Kundendatenbank. Eine öffentlich laufende Anwendung wird nicht bereitgestellt. Die Screenshots zeigen ausschließlich erfundene Daten einer eigenständigen Demo.

**Es wird keine Open-Source-Lizenz oder allgemeine Erlaubnis zur Weiterverwendung des eigenen Portfolio-Materials erteilt.** Gesetzliche Rechte, GitHubs Plattformbedingungen und Rechte Dritter bleiben unberührt. [Rechtehinweis](RIGHTS.md).
