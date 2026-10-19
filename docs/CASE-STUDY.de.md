# Scope CRM — Fallstudie

[English](CASE-STUDY.md) · [Projektübersicht](../README.de.md) · [Prüfbericht](VERIFICATION.de.md)

Ein eigenständiges, mit KI-Unterstützung entwickeltes Laravel-CRM von **LeonScope**. Das Projekt zeigt einen vollständigen Kundenablauf mit serverseitigen Berechtigungen, Terminen, Änderungsverlauf und bestätigtem CSV-Import. Es läuft lokal mit erfundenen Daten und benötigt keinen externen Geschäftsdienst.

## Wofür die Demo gedacht ist

In einem kleinen Vertriebs- oder Serviceteam müssen Kundendaten, Gesprächsnotizen und Termine zusammenpassen. Wechselt die Zuständigkeit, soll die neue Person weiterarbeiten können. Die bisher zuständige Person soll anschließend keinen Zugriff mehr haben.

Die Demo bildet das für ein Team mit zwei Rollen ab. Sie wurde neu aufgebaut, damit sich die Abläufe ohne Code oder Daten eines früheren Auftraggebers zeigen lassen.

## Umsetzung

Administratoren verwalten den gesamten Kundenbestand und die Zuweisungen. Mitarbeiter lesen und bearbeiten nur ihre eigenen aktiven Kunden. Notizen und Termine gehören zum Kunden; bei einer Neuzuweisung ändern sich die Zugriffsrechte sofort. Archiv und Wiederherstellung erhalten den Verlauf.

Der CSV-Import folgt **Upload → Vorschau → Bestätigung**. Alle Einträge müssen gültig sein. Doppelte Adressen, veränderte Zuständigkeiten, abgelaufene Vorschauen und geänderte Dateien verhindern die Übernahme. Ein erfolgreicher Import speichert sämtliche Kunden und Verlaufseinträge gemeinsam. Scheitert ein Verlaufseintrag, wird alles zurückgenommen. Wiederholtes Bestätigen legt keine weiteren Kunden an.

![CSV-Vorschau vor der Bestätigung](../assets/import-preview-desktop.png)

## Technische Entscheidungen

| Entscheidung | Begründung und Grenze |
| --- | --- |
| Laravel, Blade und eine Anwendung | Anmeldung, Validierung, Ansichten und Fachregeln bleiben zusammen. Ein separates Frontend mit eigener API würde für diesen Ablauf zusätzliche Komplexität schaffen. |
| SQLite | Die lokale Demo läuft ohne separaten Datenbankdienst. MySQL und eine hohe Zahl gleichzeitiger Zugriffe wurden nicht getestet. |
| Policies und eingeschränkte Datenabfragen | Direkte Aufrufe und Schreibzugriffe beachten dieselben Regeln wie die Oberfläche. Ein ausgeblendeter Button allein schützt keine Daten. |
| Gemeinsame Feldvalidierung | Kundenformular und CSV verwenden dieselben Längen-, Status- und Eindeutigkeitsregeln. |
| Transaktionen mit Änderungsverlauf | Geschäftsvorgang und Verlaufseintrag gelingen gemeinsam. Der Verlauf schützt nicht vor jemandem mit direktem Datenbankzugriff. |
| Private CSV-Vorschau mit Ablaufzeit | Uploads liegen außerhalb der im Browser erreichbaren Dateibereiche. Eine Prüfsumme bindet die Bestätigung an die geprüfte Datei. Fehlgeschlagene Bereinigungen bleiben für einen erneuten Versuch erfasst. |
| Durchgängig UTC | Die kleine Demo vermeidet versteckte Zeitzonenumrechnung. Ein späterer lokalisierter Kalender benötigt dafür ein eigenes Konzept. |

## Nachweise und Erkenntnisse

Die lokale Testsuite umfasst **53 Tests mit 430 Einzelprüfungen**. Vier Browserabläufe prüfen Kundenverwaltung, Berechtigungen, Tastaturbedienung, mobile Darstellung und CSV-Import. Der [Prüfbericht](VERIFICATION.de.md) ordnet Ergebnisse den tatsächlichen Quellständen und Läufen zu. Die Ergebnisse beschreiben das geprüfte Verhalten der Demo. Sie messen keine Nutzung im Produktivbetrieb oder betriebliche Einsparungen.

Zwei konkrete Erkenntnisse aus der Implementierung: Das Verlaufsfeld `changes` kollidierte mit einer internen Eloquent-Eigenschaft und musste gezielt als gespeichertes Attribut gelesen werden. Bei der Dateibereinigung war eine stabile Verarbeitung nach ID erforderlich, damit nach der Bearbeitung früherer Einträge keine späteren übersprungen werden. Beide Fälle sind durch Tests abgesichert. Auch ungültige Importe und simulierte Speicherfehler gehören zur Prüfung.

## Mein Anteil und die KI-Unterstützung

Ich habe mich für eine eigenständige CRM-Demo entschieden, den Umfang bestätigt und die Überarbeitung begleitet. Codex hat Code, Oberfläche, Beispieldaten und Tests erstellt und die dokumentierten Prüfungen ausgeführt.

Die KI-Unterstützung betrifft die Entwicklung. Das CRM selbst verarbeitet Kundendaten nach festen Regeln und verwendet kein KI-Modell.

## Ablauf einer persönlichen Vorführung

1. Demo starten: Übersicht mit 40 erfundenen Kunden, zwölf Terminen und drei lokalen Konten zeigen.
2. Einen Kunden anlegen, Demo Alex zuweisen, Notiz ergänzen und Termin planen.
3. Alex' Zugriff mit Sams verweigertem Zugriff vergleichen und anschließend als Administrator neu zuweisen.
4. Die CSV-Vorlage hochladen, Vorschau prüfen und bestätigen. Dieselbe Datei erneut hochladen, um die Duplikatprüfung zu zeigen.
5. Tests öffnen und einen Fehlerfall, eine Architekturentscheidung und eine aktuelle Grenze erklären.

## Was hier veröffentlicht ist

Die lokale Anwendung ist umgesetzt und geprüft. Dieses Repository enthält ihre Beschreibung, Screenshots und Testergebnisse. Der Quellcode bleibt privat; eine Open-Source-Lizenz wird nicht erteilt. Die Vorführung oben bezieht sich auf die lokale Demo, die nicht als Download angeboten wird.

Öffentliches Hosting, externe Kalender oder E-Mails und mehrere getrennte Kundenteams sind nicht eingebaut. Eine Prüfung unter Produktionslast wurde nicht durchgeführt. Der heutige Betrieb des früheren Kundenprojekts gehört nicht zu dieser Demo. [Rechtehinweis](../RIGHTS.md).
