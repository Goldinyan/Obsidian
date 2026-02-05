---
id: Botnet
aliases:
Topic: Explanation on what a botnet is.
Related:
  - "[[%Cyber Security]]"
  - "[[%Hardware]]"
Tags:
  - F
Date: 2026-02-05T08:00:00
Updated:
---
# Botnet

A botnet is a network of computers or devices that have been infected and remotely controlled by someone without the owners’ knowledge. 
In cybersecurity, you study botnets because they’re one of the main infrastructures behind large‑scale attacks. Including [[What is a DDoS attack?]], credential stuffing, spam campaigns, and more.

  
## What a botnet is

A botnet = bot (infected device) + network (many bots controlled together).

Each infected device is called a:

- bot
- zombie
- agent

All bots are controlled by a central system called a:

- C2 server (command‑and‑control)
- controller
- botmaster (attacker)

**The key idea:**

>The attacker can send one command, and thousands of infected devices execute it simultaneously.

  

## How a botnet is structured (conceptually)

Most botnets follow this architecture:

### Infection

Devices get compromised through:

- malware
- phishing
- exploiting vulnerabilities
- weak passwords (e.g., IoT devices with default creds)

### Enrollment

Once infected, the device:

- connects to the C2 server
- identifies itself
- waits for commands

### Operation

The attacker can instruct all bots to:

- send traffic (DDoS)
- steal data
- mine cryptocurrency
- scan for more vulnerable devices
- download additional malware
