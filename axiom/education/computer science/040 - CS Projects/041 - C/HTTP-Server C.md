Date: 2025-12-07
Tags: {
#W
[[%C]]
[[%Projects]]
[[%Computer Science]]
}


# C Projects

### Strukturplan: HTTP-Server in C

Strukturplan für einen eigenen HTTP-Server

1. Grundlagen verstehen• HTTP als Protokoll: Request/Response-Modell
• Unterschied zwischen Methoden: GET, POST, PUT, DELETE
• Statuscodes (200, 404, 500 usw.)
• Header und Body im Request/Response

2. Server-Basis aufsetzen• Socket-Programmierung: Verbindung öffnen, Ports binden (Standard: 80 oder 8080)
• Request entgegennehmen (Rohdaten lesen)
• Response zurückschicken (Rohdaten schreiben)
• Endlosschleife für mehrere Anfragen

3. Request-Verarbeitung• Parsing des HTTP-Requests: Methode, Pfad, Header, Body
• Routing: Entscheidung, welche Funktion bei welchem Pfad ausgeführt wird
• Fehlerbehandlung: ungültige Requests, unbekannte Pfade

4. Response-Erstellung• Statuszeile (z. B. HTTP/1.1 200 OK)
• Header (Content-Type, Content-Length, ggf. Cookies)
• Body (HTML, JSON, Text)
• Saubere Trennung zwischen Header und Body

5. Modularisierung• Trennung von Netzwerkcode und Logik
• Router-Komponente für Pfade
• Controller/Handler für einzelne Endpunkte
• Utility-Funktionen für Parsing und Response-Bau

6. Erweiterungen• Unterstützung für statische Dateien (HTML, CSS, JS)
• Logging von Requests und Fehlern
• Konfigurationsdatei für Ports, Pfade, Sicherheitseinstellungen
• Middleware (z. B. Authentifizierung, Caching)

7. Sicherheit und Stabilität• Input-Validierung (kein Blindes Ausführen von Nutzereingaben)
• Schutz vor gängigen Angriffen (SQL-Injection, XSS, CSRF – je nach Kontext)
• Ressourcen-Management (Timeouts, Limits für Request-Größe)
• Fehler-Handling mit klaren Statuscodes



# References