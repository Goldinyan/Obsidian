

**Dig** (Domain Information Groper) analysiert DNS (Domain Name System).
Wenn du im Browser `google.com`eingibst, muss dein PC im Hintergrund die dazugehörige IP-Adresse abfragen.

**Dig** macht genau das, aber zeigt im Gegensatz auch noch den unbeschönigten, detaillierten Rohbericht des DNS-Servers an.

Dies hilft breim prüfen, auf welche IP-Adresse eine Domain zeigt, ob es einen Fehler bei der Domain-Einrichtung gibt und ob diverse Nameserver-Änderungen schon weltweit übernommen wurden.

Aber wie funktioniert **Dig**?

**Dig** sendet eine direkte UDP- oder TXP-Anfrage auf Port 53 an einen DNS-Server. Standartmäßig ist das der Router des Providers.
Es ist wie eine gezielte Registerabfrage:
'Gib mir die Einträge für Domain X.'
Es finded dabei **keinerlei** Kontakt mit dem eigentlichen Webserver der Website statt.

#### Output

Printed standardisierter Block, aufgeteilt in drei wichtigsten Zeilen:
```bash
status: NOERROR # SUCESS, bei 'NXDOMAIN' gibt es die Domain nicht

ANSWER SECTION # Herzstück, beinhaltet Domain und IP-Adressen

SERVER: ... # Zeigt welcher DNS-Server dir die Antwort gegeben hat
```



