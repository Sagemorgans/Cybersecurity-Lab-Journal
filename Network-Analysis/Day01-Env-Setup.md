# Day 01: Virtual Lab Architecture & Provisioning

## Objective
To establish a secondary, isolated "Sandbox" for security research, ensuring that offensive operations are contained within a **Type-2 Hypervisor** to prevent host-machine contamination.

## Lab Topology
* **Hypervisor:** VirtualBox 7.x
* **Attacker Node:** Kali Linux 2026.1 (Rolling)
* **Victim Node:** Ubuntu 24.04 LTS (Desktop)

## Implementation Steps

### 1. Resource Allocation
To ensure high-performance packet capture without system lag, the following hardware offsets were assigned:
* **Kali Linux:** 4GB RAM | 2 Processors
* **Ubuntu:** 4GB RAM | 1 Processor

### 2. Networking Strategy: The NAT to Bridged Pivot -virtualbox
Initially, the VMs were set to **NAT Mode** for secure internet access during tool installation. However, for the **ARP Poisoning** labs, the strategy was shifted:
* **Configuration:** Switched to **Bridged Adapter**.
* **Promiscuous Mode:** Enabled **"Allow All"** to permit the virtual NIC to see traffic not specifically addressed to its MAC.



### 3. Baseline Hardening
Before testing, both nodes were baseline-patched:
```bash
sudo apt update && sudo apt upgrade -y
