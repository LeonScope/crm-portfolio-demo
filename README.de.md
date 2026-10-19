# Scope CRM

### Kundenarbeit mit klaren Zuständigkeiten.

**Geschäftsanwendung · Laravel · Lokale Portfolio-Demo**

[English](README.md) · [Fallstudie](docs/CASE-STUDY.de.md) · [Prüfergebnisse](docs/VERIFICATION.de.md)

Ein Kundeneintrag hilft, wenn die nächste Person erkennt, wer zuständig ist, was besprochen wurde und welcher Schritt ansteht. Scope CRM verbindet Zuständigkeiten, Termine, Notizen und Änderungsverlauf in einem Arbeitsbereich. Von **[LeonScope](https://github.com/LeonScope)** mit KI-Unterstützung als eigenständige Demo mit erfundenen Daten entwickelt.

![Scope CRM mit Teamübersicht, Terminen und direktem Zugang zum CSV-Import](assets/dashboard-desktop.png)

## Ein Arbeitstag im CRM

| Aufgabe | Sichtbares Verhalten |
| :--- | :--- |
| Gespräch vorbereiten | Kunden finden, Notizen lesen und anstehende Termine sehen. |
| Verantwortung zuweisen | Administratoren verwalten den Teambestand; Mitarbeiter bearbeiten ihre zugeordneten Kunden. Der Server setzt die Zugriffsregeln durch. |
| Änderungen nachvollziehen | Kunden- und Terminänderungen werden gemeinsam mit ihren Verlaufseinträgen gespeichert. |
| Neue Kunden übernehmen | CSV hochladen, jede Zeile prüfen und erst anschließend den Import bestätigen. |

Die überarbeitete Übersicht stellt die Kundenarbeit in den Mittelpunkt: kompakte Einführung, sichtbare Rolle und direkter Zugang zur Kundenliste sowie zum Import für Administratoren. Die grüne Geschäftsoberfläche erhält die vertraute Navigation.

## Import mit Prüfschritt

**Upload → Prüfung und Vorschau → ausdrückliche Bestätigung.** Ungültige Importe legen keine Kunden an. Geprüft werden unter anderem Duplikate, archivierte Einträge, Zuständigkeiten, abgelaufene Vorschauen und veränderte Dateien. Der Import ergänzt neue Kunden; bestehende Datensätze werden nicht aktualisiert.

![CSV-Importvorschau mit Prüfung vor der Bestätigung](assets/import-preview-desktop.png)

<details>
<summary><strong>Smartphone-Ansichten</strong> — Kundensuche und Importfehler</summary>

<table><tr>
<td valign="top"><strong>Kundenliste</strong><br /><img src="assets/customers-mobile.png" width="300" alt="Mobile Kundenliste mit Suche" /></td>
<td valign="top"><strong>Importprüfung</strong><br /><img src="assets/import-errors-mobile.png" width="300" alt="Mobile CSV-Vorschau mit ungültigen und doppelten Einträgen" /></td>
</tr></table>

</details>

## Was dieses Projekt belegt

Rollenbasierte Abläufe, gemeinsam gespeicherte Änderungen und Verlaufseinträge sowie einen abgesicherten Datenimport mit **Laravel 13, PHP 8.4, Blade, SQLite und Vite**. Die lokale Demo startet mit 40 erfundenen Kunden und drei erzeugten Konten.

**53 Anwendungstests mit 430 Einzelprüfungen und vier Browserabläufe bestanden.** Die Oberfläche wurde am 19. Oktober 2026 erneut geprüft; die frühere Prüfung nach frischer Installation bleibt gesondert dokumentiert. [Ergebnisse, Umgebung und Grenzen](docs/VERIFICATION.de.md).

LeonScope legte das Portfolioziel fest, bestätigte Produktrichtung und Umfang und steuerte die Iterationen. Codex erzeugte Implementierung, Oberfläche, Beispieldaten und Tests und führte die dokumentierten Prüfungen aus. Das CRM selbst ruft kein KI-Modell auf.

## Zugang zum Projekt

Dieses Repository enthält **ausschließlich die Präsentation** einer funktionsfähigen lokalen Anwendung. Quellcode, Zugangsdaten, Datenbanken und Installationspakete bleiben privat. Es gibt keine öffentlich gehostete Anwendung und keine öffentliche Anwendungs-CI. Die eigenständige Demo enthält weder Quellcode noch Geschäftsdaten des früheren Auftraggebers.

Es wird keine Open-Source-Lizenz, Creative-Commons-Lizenz oder allgemeine Erlaubnis zur Weiterverwendung des eigenen Portfolio-Materials erteilt. Gesetzliche Rechte, GitHubs Plattformbedingungen und Rechte Dritter bleiben unberührt. [Rechtehinweis](RIGHTS.md).

[Fallstudie und Vorführung](docs/CASE-STUDY.de.md) · [Prüfergebnisse](docs/VERIFICATION.de.md) · [LeonScope](https://github.com/LeonScope)
