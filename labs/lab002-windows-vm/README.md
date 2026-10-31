# Lab 2 — A Windows guest, and a network between them

**Pair:** Anuar / Ayanat  
**Driver first half:** Anuar  
**Machine:** AMD Ryzen 5 7535HS, Windows 11, 16 GB RAM, 6 cores / 12 threads. Guests: Ubuntu Server + Windows 11 Enterprise Evaluation.  
**Date:** 31.10.2026

## What I did

1. Downloaded Windows 11 Enterprise Evaluation from the [Microsoft Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-11-enterprise).
2. Created `lab02-windows`: 2 vCPU, 4 GB RAM, 64 GB dynamically allocated disk, UEFI + Secure Boot, vTPM 2.0.
3. Network mode: **NAT Network** (the same network for both guests). Reason: both virtual machines need internet access and direct communication with each other. Regular NAT gives each VM a separate virtual network.
4. Ubuntu → Windows initially timed out. The network configuration and Windows Firewall need to be checked. If the firewall blocks ICMP requests, the following PowerShell rule allows incoming IPv4 ping requests:

```powershell
New-NetFirewallRule -DisplayName "Allow ICMPv4 Echo" -Protocol ICMPv4 -IcmpType 8 -Direction Inbound -Action Allow
```

5. Memory allocation: 2 GB for Ubuntu + 4 GB for Windows = 6 GB allocated to virtual machines on a 16 GB host.

## Network diagram

```text
              Internet
                  |
             VirtualBox
              NAT Network
              /        \
             /          \
      Ubuntu Server   Windows 11
       2 GB RAM        4 GB RAM
       2 vCPU          2 vCPU
```

## Result

| | Before | After |
|---|---|---|
| Host RAM in use |8|  15| 
| Available |6.9 GB | 337 MB| 
| Committed / Swap used | 19.2 | 25.9 |
| What I noticed | — | The memory usgae spiked to the limit. PC started working slowly then usual. Overall, consumption of power and memory was noticeable|

## What did not work the first time

The Ubuntu guest successfully accessed the internet using `ping -c 4 ubuntu.com`. However, internet connectivity alone does not prove that the two virtual machines can communicate.

Regular NAT can isolate the guests because each VM has its own NAT engine. The solution is to configure both guests to use the same NAT Network. Windows Firewall may also block incoming ICMP requests, so an inbound ICMPv4 rule can be added if necessary.



## Evidence

- [evidence/ipconfig-windows.png](evidence/ipconfig-windows.png) — Windows IP configuration.
- [evidence/ip addr linux.png](evidence/ip-addr-linux.png) — Ubuntu IP configuration.
- [evidence/ping both ways lin.png](evidence/ping-both-ways-lin.png) — connectivity tests in both directions and internet connectivity.
- [evidence/hostmemorybefore.png](evidence/host-memory-before.png) — host memory, both guests off.
- [evidence/hostmemoryafter.png](evidence/host-memory-after.png) — host memory, both guests running.