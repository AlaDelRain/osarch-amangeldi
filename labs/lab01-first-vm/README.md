\# Lab 1 — Your first virtual machine



Pair: AnuarKhan / Ayanat   Driver first half: <name>

Machine:  Windows 11 host, Ubuntu Server guest

Date: <25.10.2026)



\## What I did

Installed Oracle VirtualBox. Licence: https://www.virtualbox.org/wiki/Licensing\_FAQ



Created VM lab01-ubuntu with the configured CPU and RAM, a 25 GB virtual disk, and NAT networking.



Installed Ubuntu Server and created a snapshot named clean-install.



Broke the system by removing /etc/hostname using sudo rm /etc/hostname.



Rolled back to the clean-install snapshot and checked whether the hostname file and system were restored.





Resource justification



The virtual machine was configured with a limited amount of CPU cores and RAM to leave enough resources for the Windows host to operate smoothly. The virtual disk was set to 25 GB with dynamic allocation to avoid occupying the full amount of disk space immediately. The actual allocation was based on the host computer's available resources.



Result



The VM was configured for Ubuntu Server with NAT networking. The break-and-rollback procedure was attempted using the clean-install snapshot. Successful recovery should be confirmed by checking the hostname file and verifying that Ubuntu boots normally.



What did not work the first time



When entering a command in the terminal, I accidentally left a single quotation mark unclosed. Bash displayed the continuation prompt > and treated subsequent input as part of the unfinished command. I cancelled it with Ctrl+C and corrected the command syntax.



I also initially entered an SSH command without a space before the quoted command, which caused a hostname parsing error. I corrected the command syntax.





\## Evidence

\- \[evidence/vm-settings.png](evidence/vm-settings.png) — CPU, memory and disk as configured

\- \[evidence/guest-release.txt](evidence/guest-release.txt) — Ubuntu Server is running in the guest

\- \[evidence/broken.png](evidence/broken.png) — the guest in its broken state

\- \[evidence/snapshot-list.png](evidence/snapshot-list.png) — the snapshot, after the rollback

