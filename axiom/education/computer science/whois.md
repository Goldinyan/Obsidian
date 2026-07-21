

`whois`  is a query tool used to look up information in a worldwide, decentralized database that stores the registration details of all domains and IP address blocks. Every time someone buys a domain, they are legally required to provide contact information to the registrar.

You need it to:

- Find out who officially owns a domain.
- Identify the domain registrar (the company where the domain was bought, e.g., GoDaddy, Namecheap, Ionos).
- Find administrative or technical contact details (Admin-C / Tech-C) to report abuse, spam, or security issues.
- Check when a domain was registered and when it is set to expire.


#### How does it work under the hood?

`whois` establishes a TCP connection over **Port 43** to the WHOIS server run by the respective registry. For example, if you query a `.de` domain, it queries *DENIC*. If you query a `.com` domain, it contacts the *Verisign* database.

Just like `dig`, **the actual web server of your target never notices this scan.** The entire query is handled completely by the registries' third-party databases.


### Essential Options & Commands

`whois` is straightforward and rarely requires complex flags because it dumps the full record by default. However, a few options are good to know:


```bash
whois traget.com # Standard domain query. Displays all owner, registers, and data records

whois 142.250.161.98 # Querys an IP address instead of a domain. Finds out which provider owns an IP ranfe

whois -h whois.denic.de target.de # Forces the query through a specific WHOIS server via the -h flag
```

### Reading the Output (Key Fields to Look For)

WHOIS outputs can be massive walls of text, but you usually only need to scan for these specific key-value pairs:

- **`Registrar`**: The company managing the domain registration (e.g., *MarkMonitor Inc.* for Google).
- **`Creation Date` / `Registered On`**: The exact date the domain was first registered.
- **`Registry Expiry Date` / `Expiration Date`**: The deadline when the domain will expire if not renewed.
- **`Status` / `Domain Status`**: Shows if the domain is active (often reads `clientTransferProhibited`, which is a security lock preventing unauthorized domain theft/transfers).
- **`Registrant/Admin/Tech Contact`**: The name, physical address, and email of the owner.

**Privacy Note (GDPR):** Since the introduction of GDPR, you will rarely see real names, private phone numbers, or physical addresses for European domains or citizens. 
Most fields will simply display "REDACTED FOR PRIVACY" or mask the identity using the registrar's proxy data.

