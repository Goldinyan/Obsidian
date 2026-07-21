
`nslookup` is a command-line tool used to query Domain Name System (DNS) servers to find IP addresses associated with a domain name, or vice versa.

You need it to:

- Quickly check if a domain resolves to the correct IP.
- Run quick tests on Windows machines where `dig` isn't natively available.
- Perform reverse DNS lookups (finding the domain name that belongs to a specific IP address).


### How does it work under the hood?

Like `dig`, `nslookup` talks exclusively to DNS servers over **Port 53 (UDP/TCP)**. It does not contact the web server hosting the website.

One unique feature of `nslookup` is that it can be used in two modes:

1. **Interactive Mode:** You type `nslookup`, press Enter, and enter a dedicated shell where you can run multiple queries in a row.
2. **Non-Interactive Mode:** You run a single command and get an immediate output (just like `dig`).


### Essential Options & Commands

```bash
nslookup target.com # Standard query for a domain. Finds the IPv4 and IPv6 addresses of the domain

nslookup -type=mx google.com # Looks for Mail Exnchange (MX) records. Checks which mail severs handle emails for that domain.

nslookup -type=ns target.com # Lools for Name Server (NS) records. Finds out which DNS servers are authoritative for the domain 

nslookup 142.250.161.98 # Reverse DNS Lookup. Converts an IP address back into a domain name.

nslookup target.com 8.8.8.8 # Queries a specific DNS server. Forces the tool to ask Target's public DNS (8.8.8.8) instead of your local router.
```


### Reading the Output

`nslookup` outputs are much shorter and more minimalist than `dig`. A typical output looks like this:

```text
Server:		192.168.178.1
Address:	192.168.178.1#53

Non-authoritative answer:
Name:	google.com
Address: 142.250.161.98
```

- **`Server` / `Address` (Top half):** This is the DNS server that *answered* your request (e.g., your local Fritz!Box or home router).
- **`Non-authoritative answer`**: This means the DNS server you asked doesn't *own* the original record. It just looked it up from its cache or passed the question along to a parent server.
- **`Name` / `Address` (Bottom half):** This is your actual result. The domain name you looked up and the IP address it points to.

