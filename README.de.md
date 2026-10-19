# Scope CRM

### Kunden, Termine und Zuständigkeiten an einem Ort

**Geschäftsanwendung · Laravel · Lokale Portfolio-Demo**

[English](README.md) · [Fallstudie](docs/CASE-STUDY.de.md) · [Prüfergebnisse](docs/VERIFICATION.de.md)

Scope CRM ist eine lokale Demo für die Kundenarbeit in einem kleinen Team. Zu jedem Kunden gehören eine zuständige Person, Gesprächsnotizen und Termine. Ein Änderungsverlauf hält fest, was bearbeitet wurde. Das Projekt entstand mit KI-Unterstützung und verwendet ausschließlich erfundene Daten.

![Scope CRM mit Teamübersicht, Terminen und direktem Zugang zum CSV-Import](assets/dashboard-desktop.png)

## Ein Arbeitstag im CRM

| Aufgabe | So funktioniert es |
| :--- | :--- |
| Gespräch vorbereiten | Kunden finden, Notizen lesen und anstehende Termine sehen. |
| Verantwortung zuweisen | Administratoren verwalten den Teambestand; Mitarbeiter bearbeiten ihre zugeordneten Kunden. Der Server setzt die Zugriffsregeln durch. |
| Änderungen nachvollziehen | Kunden- und Terminänderungen werden gemeinsam mit ihren Verlaufseinträgen gespeichert. |
| Neue Kunden übernehmen | CSV hochladen, jede Zeile prüfen und erst anschließend den Import bestätigen. |

Auf der Startseite stehen anstehende Termine und die letzten Änderungen. Administratoren sehen den Teambestand und gelangen von dort auch zum CSV-Import. Mitarbeiter sehen die Kunden, für die sie zuständig sind.

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

## Technik und Tests

Die Anwendung verwendet **Laravel 13, PHP 8.4, Blade, SQLite und Vite**. Bei der ersten Einrichtung werden 40 erfundene Kunden und drei lokale Konten angelegt.

Am 19. Oktober 2026 bestanden erneut **53 Anwendungstests mit 430 Einzelprüfungen und vier Browserabläufe**. Der [Prüfbericht](docs/VERIFICATION.de.md) beschreibt die Testumgebung, die geprüften Fälle und die frühere Neuinstallation vom 18. Oktober.

Ich habe die Richtung und den Umfang der Demo festgelegt und die Überarbeitung begleitet. Codex hat Code, Oberfläche, Beispieldaten und Tests erstellt und die dokumentierten Prüfungen ausgeführt. Die KI kam bei der Entwicklung zum Einsatz; das CRM selbst arbeitet ohne KI-Modell.

## Veröffentlichung

Hier sind **die Projektbeschreibung und Screenshots** veröffentlicht. Die Anwendung läuft lokal; Quellcode, Zugangsdaten, Datenbank und Installationspakete bleiben privat. Es gibt keinen öffentlichen Demozugang und keinen Anwendungstestlauf auf GitHub. Die Demo wurde neu aufgebaut und enthält keinen Code oder Geschäftsdaten meines früheren Auftraggebers.

Für das eigene Material wird keine Open-Source- oder Creative-Commons-Lizenz und keine allgemeine Nutzungserlaubnis erteilt. Die Einzelheiten stehen im [Rechtehinweis](RIGHTS.md).

[Fallstudie und Vorführung](docs/CASE-STUDY.de.md) · [Prüfergebnisse](docs/VERIFICATION.de.md) · [LeonScope](https://github.com/LeonScope)
