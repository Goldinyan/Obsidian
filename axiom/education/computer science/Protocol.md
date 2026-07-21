Date: 2026-01-20
Tags: {
#F 
[[%Communication]]
[[%Network]]
[[%Protocol]]
}


# Protocol

A protocol is a precisely defined set of rules that governs how two or more systems communicate. It specifies how data is structured, transmitted, interpreted, and responded to so that different machines can reliably exchange information, even if they use different hardware or software.

## Core idea

A protocol is essentially a contract:

If both sides follow the same rules, communication works. If not, it breaks.

### What a protocol defines

**Message format**
How bits/bytes are arranged, packet structure, headers, fields, checksums.

**Syntax**
What messages look like (e.g., “GET /index.html HTTP/1.1”).

**Semantics**
What each message means and what actions it triggers.

**Order / sequencing**
Who speaks first, how responses must follow, how to handle timeouts.

**Error handling**
Retransmissions, acknowledgements, recovery strategies.

**State machines**
Many protocols define explicit states (e.g., TCP’s SYN -> SYN/ACK -> ACK).

### Why protocols matter

Without protocols, devices would talk past each other, like one speaking in 8‑bit chunks and the other expecting 16‑bit chunks.

Key properties

- Standardized (IETF, ISO, IEEE) so everyone implements the same rules.
- Implementation‑agnostic: hardware, OS, and language don’t matter as long as the rules are followed.
- Deterministic: given a message, the protocol defines exactly what must happen.


# Summary

>A protocol is a precisely defined set of rules that governs how two or more systems communicate. It specifies how data is structured, transmitted, interpreted, and responded to so that different machines can reliably exchange information, even if they use different hardware or software.

# References