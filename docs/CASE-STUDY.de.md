# CRM Portfolio Demo — Fallstudie

[English](CASE-STUDY.md) · [Projektübersicht](../README.de.md) · [Prüfbericht](VERIFICATION.de.md)

Ein eigenständiges, mit KI-Unterstützung entwickeltes Laravel-CRM von **LeonScope**. Das Projekt zeigt einen vollständigen Kundenablauf mit serverseitigen Berechtigungen, Terminen, Änderungsverlauf und bestätigtem CSV-Import. Es läuft lokal mit erfundenen Daten und benötigt keinen externen Geschäftsdienst.

## Ausgangsproblem

Ein kleines Vertriebs- oder Serviceteam muss vier Fragen beantworten können: Wer ist der Kunde? Wer ist zuständig? Was wurde besprochen? Was passiert als Nächstes? Der Ablauf soll auch dann stimmen, wenn Zuständigkeiten wechseln, Kunden archiviert oder Tabellen importiert werden.

Die Demo bildet dieses Szenario mit bewusst begrenztem Umfang ab: ein Team, zwei Rollen und wenige miteinander verbundene Abläufe. Das Ergebnis lässt sich prüfen, ohne Quellcode oder Daten eines früheren Auftraggebers zu verwenden.

## Umsetzung

Administratoren verwalten den gesamten Kundenbestand und die Zuweisungen. Mitarbeiter lesen und bearbeiten nur ihre eigenen aktiven Kunden. Notizen und Termine gehören zum Kunden; bei einer Neuzuweisung ändern sich die Zugriffsrechte sofort. Archiv und Wiederherstellung erhalten den Verlauf.

Der CSV-Import folgt **Upload → Vorschau → Bestätigung**. Alle Einträge müssen gültig sein. Doppelte Adressen, veränderte Zuständigkeiten, abgelaufene Vorschauen und geänderte Dateien verhindern die Übernahme. Ein erfolgreicher Import speichert sämtliche Kunden und Verlaufseinträge gemeinsam. Scheitert ein Verlaufseintrag, wird alles zurückgenommen. Wiederholtes Bestätigen legt keine weiteren Kunden an.

![CSV-Vorschau vor der Bestätigung](../assets/import-preview-desktop.png)

## Technische Entscheidungen

| Entscheidung | Begründung und Grenze |
| --- | --- |
| Laravel, Blade und eine Anwendung | Anmeldung, Validierung, Ansichten und Fachregeln bleiben zusammen. Ein separates Frontend mit eigener API würde für diesen Ablauf zusätzliche Komplexität schaffen. |
| SQLite | Die Demo lässt sich ohne Datenbankdienst starten. Daraus folgt kein Nachweis für MySQL oder hohe gleichzeitige Produktionslast. |
| Policies und eingeschränkte Datenabfragen | Direkte Aufrufe und Schreibzugriffe beachten dieselben Regeln wie die Oberfläche. Ein ausgeblendeter Button allein schützt keine Daten. |
| Gemeinsame Feldvalidierung | Kundenformular und CSV verwenden dieselben Längen-, Status- und Eindeutigkeitsregeln. |
| Transaktionen mit Änderungsverlauf | Geschäftsvorgang und Verlaufseintrag gelingen gemeinsam. Der Verlauf schützt nicht vor jemandem mit direktem Datenbankzugriff. |
| Private CSV-Vorschau mit Ablaufzeit | Uploads liegen außerhalb der im Browser erreichbaren Dateibereiche. Eine Prüfsumme bindet die Bestätigung an die geprüfte Datei. Fehlgeschlagene Bereinigungen bleiben für einen erneuten Versuch erfasst. |
| Durchgängig UTC | Die kleine Demo vermeidet versteckte Zeitzonenumrechnung. Ein späterer lokalisierter Kalender benötigt dafür ein eigenes Konzept. |

## Nachweise und Erkenntnisse

Die lokale Testsuite umfasst **53 Tests mit 430 Einzelprüfungen**. Vier Browserabläufe prüfen Kundenverwaltung, Berechtigungen, Tastaturbedienung, mobile Darstellung und CSV-Import. Der [Prüfbericht](VERIFICATION.de.md) ordnet Ergebnisse den tatsächlichen Quellständen und Läufen zu. Diese Zahlen belegen geprüfte Softwareabläufe; sie sind keine erfundenen Nutzer- oder Einsparungskennzahlen.

Zwei konkrete Erkenntnisse aus der Implementierung: Das Verlaufsfeld `changes` kollidierte mit einer internen Eloquent-Eigenschaft und musste gezielt als gespeichertes Attribut gelesen werden. Bei der Dateibereinigung war eine stabile Verarbeitung nach ID erforderlich, damit nach der Bearbeitung früherer Einträge keine späteren übersprungen werden. Beide Fälle sind durch Tests abgesichert. Auch ungültige Importe und simulierte Speicherfehler gehören zur Prüfung.

## Rolle und KI-Unterstützung

LeonScope legte das Portfolioziel fest, bestätigte die eigenständige Produktrichtung und den Funktionsumfang und steuerte die Iterationen. Codex erzeugte Implementierung, Oberfläche, Beispieldaten und Tests und führte die dokumentierten Prüfungen aus. Die Unterstützung ist offengelegt; der Code wird nicht als vollständig manuell geschrieben dargestellt.

Das Projekt zeigt den Weg von Anforderungen zu einer prüfbaren Anwendung mit klaren Grenzen und dokumentierten Korrekturen. Das CRM ruft kein KI-Modell auf und behauptet keine KI-Produkteigenschaft. LeonScopes frühere Erfahrung mit Robotik und kameragestützter Prüfung ist eigenständiger beruflicher Hintergrund; diese Demo ist eine neue Webanwendung.

## Ablauf einer persönlichen Vorführung

1. Demo starten: Übersicht mit 40 erfundenen Kunden, zwölf Terminen und drei lokalen Konten zeigen.
2. Einen Kunden anlegen, Demo Alex zuweisen, Notiz ergänzen und Termin planen.
3. Alex' Zugriff mit Sams verweigertem Zugriff vergleichen und anschließend als Administrator neu zuweisen.
4. Die CSV-Vorlage hochladen, Vorschau prüfen und bestätigen. Dieselbe Datei erneut hochladen, um die Duplikatprüfung zu zeigen.
5. Tests öffnen und einen Fehlerfall, eine Architekturentscheidung und eine aktuelle Grenze erklären.

## Stand der Präsentation

Der lokale Funktionskern ist umgesetzt und geprüft. Dieses öffentliche Repository enthält Fallstudie, Screenshots und eine Zusammenfassung der lokalen Prüfungen. Der Anwendungscode bleibt privat; eine Open-Source-Lizenz wird nicht erteilt. Die oben beschriebene Vorführung bezieht sich auf die lokale Anwendung, nicht auf einen öffentlichen Download. Eine öffentliche Bereitstellung, externe Kalender/E-Mails, Mandantenfähigkeit, Produktionslast-Prüfung oder der aktuelle Betrieb eines früheren Kundenprojekts werden nicht behauptet. [Rechtehinweis](../RIGHTS.md).
