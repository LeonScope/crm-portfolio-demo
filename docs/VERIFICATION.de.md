# Lokaler Prüfbericht

[English](VERIFICATION.md) · [Projektübersicht](../README.de.md)

Diese Ergebnisse stammen aus der privaten, eigenständig entwickelten CRM-Anwendung und wurden am **18. Oktober 2026 lokal geprüft**. Das Präsentationsrepository enthält keine Anwendungstests und behauptet keinen Prüflauf der Anwendung auf GitHub. Detaillierte Protokolle, Quellcode und erzeugte Zugangsdaten werden nicht veröffentlicht.

| Prüfung | Beobachtetes Ergebnis |
| --- | --- |
| Anwendungstests | **53 Tests, 430 Einzelprüfungen; keine Fehler oder übersprungenen Tests** |
| Browserprüfung | **Alle 4 Abläufe in einem Lauf bestanden**, ohne Fehlschläge, übersprungene Tests oder Wiederholungen |
| Browserumfang | Kunden und Termine, Rollen, Neuzuweisung, Archiv/Wiederherstellung, mobile Navigation/Suche, Tastatur-Anmeldung, Schutz vor ungültigen Anfragen und CSV-Import |
| CSV-Verhalten | **34 Anwendungsfälle** für Feld-/Formatfehler, Grenzen, Duplikate und Archivkonflikte, Zuständigkeit, Ablauf, Dateiveränderungen, Wiederholung, Rücknahme und Bereinigungsfehler |
| Frische Einrichtung | Abhängigkeiten aus Lockfiles installiert; zuvor keine Umgebung, Datenbank, Zugangsdaten oder installierten Pakete in der Prüfkopie |
| Einrichtung und Wiederholung | 40 erfundene Kunden, 3 Konten, 12 Termine; erneute Einrichtung erhielt Datenbankinhalte und erzeugte Zugangsdateien |
| Code und Browserdateien | Strenge Composer-Validierung, vollständige PHP-Codeprüfung und Produktionsbuild erfolgreich |
| Bekannte Schwachstellen | Composer: keine gemeldeten Schwachstellen oder aufgegebenen Pakete; npm: keine gemeldeten Schwachstellen zum Prüfzeitpunkt |
| Anwendungshistorie | Gitleaks fand keine Zugangsdaten in der Historie mit 10 Commits; eine zusätzliche Suche fand keine privaten Dateipfade oder früheren Projektkennungen |
| Lokale Umgebung | macOS 26.6, PHP 8.4.23, Composer 2.10.1, Node 24.19.0, Google Chrome 155.0.8059.84 |
| Ansichten | Desktop 1440 × 1060, Smartphone 390 × 844; kein seitliches Überlaufen der geprüften Seiten; die mobile CSV-Tabelle lässt sich bewusst horizontal verschieben |

Der vollständige Lauf in der frischen Kopie ersetzt die früher getrennten Browserprüfungen als aktuellen Nachweis. Die Screenshots wurden mit demselben Anwendungsstand und erfundenen Daten aufgenommen. Schreibende Browserprüfungen verwendeten eine getrennte Prüfkopie.

Für die private Anwendung liegt eine GitHub-Actions-Konfiguration vor. Sie wurde nicht auf GitHub ausgeführt und gehört nicht zu dieser Präsentation. Ein öffentlicher Anwendungstestlauf, ein herunterladbarer Software-Release und eine gehostete Anwendung sind nicht Bestandteil dieses Repositorys.

Die Prüfungen belegen keine Sicherheitszertifizierung, Produktionslastfähigkeit, MySQL-Unterstützung, Safari-/Firefox-Abdeckung oder Barrierefreiheitszertifizierung. Die Abhängigkeitsprüfung gilt für ihren Zeitpunkt. Gleichzeitige Bearbeitungskonflikte und Terminkollisionen liegen außerhalb des Demo-Umfangs. CSV-Importe legen neue Kunden an; bestehende Kunden werden nicht aktualisiert.
