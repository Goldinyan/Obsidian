Date: 2025-12-07
Tags: {
#W
[[%C]]
[[%Computer Science]]
}


# C Projects





### Strukturplan: HTTP-Server in C

Ziel: Minimaler Server, der HTTP-Anfragen entgegennimmt und eine Antwort zurückgibt.

Bausteine:

1. Socket erstellen → TCP/IP Socket öffnen.
2. Adresse konfigurieren → IP + Port festlegen.
3. Socket binden → Socket mit Adresse verbinden.
4. Lauschen → Server wartet auf eingehende Verbindungen.
5. Verbindung akzeptieren → Client wird angenommen.
6. Anfrage lesen → HTTP-Request aus dem Socket auslesen.
7. Antwort schreiben → HTTP-Response mit Header + Body zurücksenden.
8. Verbindung schließen → Socket für den Client schließen.
9. Loop → Zurück zu Schritt 5 für den nächsten Client.Date:



# References