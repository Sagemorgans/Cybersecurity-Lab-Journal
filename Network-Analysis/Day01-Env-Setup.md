# Day 01: Lab Architecture

## Objective
To build a safe "Sandbox" for security testing that won't interfere with my host computer.

## Technical Specs
- **Kali Linux:** 4GB RAM, 2 CPUs (The Attacker)
- **Ubuntu:** 4GB RAM, 1 CPU (The Victim)
- **Network:** Switched from **NAT** to **Bridged Mode** to allow the VMs to "talk" to each other at the MAC address level.

## Key Learning
I learned that **NAT** keeps VMs in a private basement, but **Bridged Mode** lets them out onto the real network so we can test ARP spoofing.
