
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

3. Observations & Performance Constraints

*Actual Findings:*
* successful Interception: Confirmed that Kali successfully positioned itself in the traffic path, as evidenced by a massive influx of packets in the Wireshark capture window.
* Hardware Bottleneck: Encountered significant system latency and "lag" once the ARP spoofing and Wireshark capture were running simultaneously.
* Resource Exhaustion: The overhead of processing real-time network traffic in a virtualized environment led to high CPU/RAM utilization, limiting the ability to perform deep packet inspection (DPI) in this specific session.

*Technical Reflection:*
This lab demonstrated that Man-in-the-Middle attacks are not "silent" or "free"—they require significant computational resources. In a production environment, an attacker would likely use `tcpdump` (command line) instead of the Wireshark GUI to save resources and avoid detection via system lag.
