# Ticket 1 — “New developer starts Monday, needs a test machine”

Hello! welcome to your new job, i will help you with setting the machine correctly. Aigerim asked me to do it, so you can try working without breaking something important and etc.

This guide will be broken down in 2 segments. First is for Linux, second is for Windows. Lets get started!

Linux installation guide:

We will assume that you already have running pc with Windows in it. What we will need is: CPU model, core count and thread count, total memory, the number of installed modules and their speed. Disk model, its type (HDD, SATA SSD, NVMe), the free space on the volume you will store VMs on and whether hardware virtualization is present and enabled. These values are important for correct usage and functioning

We shall find those parameters in WINDOWS operating system.

(Note that most of the all the searching operations about your system will be done by using task manager. It is the fastest and most efficient way to find info about your pc, programs that are running and etc. Learn how to use it, knowing how to work with it will make your work much easier in future.)

**ABOUT YOUR PC**

1) CPU model, core count and thread count: Those values could be found via task manager. Press Ctrl Shift Esc and the same time or just type "Task Manager" in search bar, click the Performance tab on the left sidebar. Select CPU, Look at the bottom-right corner for:

Cores: Your physical processor cores.

Logical processors: Your total thread count (includes Hyper-Threading or SMT). Your full CPU model name is displayed at the top right of the window.

There you could see aforementioned parameters. Write those down or keep them in mind.

2) total memory, the number of installed modules and their speed could be found with the same method: task manager. Click the Performance tab on the left sidebar, then select Memory. 

View your Total RAM in the upper-right corner

look at the bottom details for Speed (in MHz or MT/s), Slots used (e.g., "2 of 4").

3) Disk model, its type (HDD, SATA SSD, NVMe): you know the drill, task manager -> Click on the Performance tab on the left sidebar. -> Click on Disk 0 (or Disk 1, etc.).

The disk model number is shown at the top right, and the type (HDD or SSD) is listed near the bottom.

4) free space on the volume you will store VMs: This one is little tricky. You saw that your disk holds certain amount of free space (check disk model if you do not know how to find it). The VM (Virtual Machine) must NOT have lower then 3-5% and NOT higher then 85% of your disk memory dedicated for it. Why those numbers? so it may work without any errors. Go lower or higher and you could face some problems.

5) hardware virtualization is present and enabled: task manager, performance tab and select CPU. 

Look at the bottom-right for Virtualization (it will say Enabled or Disabled). Disabled? enable it.

**LINUX INSTALLATION**

Here we start our process of setting up VM.

We shall use the VirtualBox program. You may use other VMs, but in this guide it is recommended to use Virtual Box.

1) Go to https://www.virtualbox.org/wiki/Downloads and install with the defaults. It will take from 15-30 minutes.

2) Ubuntu Server ISO: We assume that you did not received USB stick or local share, so we shall download it from internet as well.

Go to ubuntu.com/download/server for amd64, or ubuntu.com/download/server/armfor ARM64. Take the current LTS release.

3) Decide the resources: Do not just accept the defaults. Each Vm requires individual resources managment. Remeber what we done in section above? Now its time to look at those numbers and input correct parametres based on them.

vCPU: 2 — never more than half of your host's cores.

Memory: 2 GB if your PC has 8 GB; 4 GB if it has 16 GB or more. Leave the host(your pc) enough for itself.

Disk: 25 GB, dynamically allocated (grows as needed).

Network: NAT.

4) Create the virtual machine:

Machine → New. Name YourName-ubuntu, ISO Image: your Ubuntu Server ISO, Type Linux, Version Ubuntu (64-bit).

Tick Skip Unattended Installation — you want to see the real installer.

Base Memory and Processors: your numbers from above.

Hard disk: Create a virtual hard disk now, 25 GB, leave Pre-allocate Full Size unticked.

Finish. Open Settings → Network: Adapter 1 should be NAT (the default).

5) Install Ubuntu Server:

Start the VM. Click inside the window to type into it. To get the mouse back out: Ctrl+Alt.

Boot menu: choose Try or Install Ubuntu Server.

Language: English. If offered an installer update, you can skip it.

Keyboard: English (US).

Type of install: Ubuntu Server (not minimized).

Network: the network card should get an address automatically (DHCP), something like 192.168.x.x or 10.0.2.15. Continue.

Proxy: leave empty. Mirror: accept the default and wait for the test to pass.

Storage: Use an entire disk. This is the 25 GB virtual disk — your laptop's real disk is safe. Accept the summary and confirm Continue.

Profile:

Your name: your name.

Server name: ubuntu-<surname>, for example ubuntu-surname.

Username: short, lowercase, for example amangeldi.

Password: one you will remember. Write it down on paper.

Ubuntu Pro: Skip for now.

SSH: tick Install OpenSSH server. You will use it below to copy text out of the VM, and again in Lab 2.

Featured server snaps: select nothing. Continue.

Wait for Installation complete!, then choose Reboot Now. If you see "Please remove the installation medium, then press ENTER", just press Enter.

Log in with your username and password. Nothing appears while you type the password — that is normal.

6) Check all systems and VM.

Inside the VM, run:

lsb_release -a

hostname

nproc

free -h

df -h /

ip -br a

You should see the Ubuntu version, your server name, your vCPU count, your memory, about 25 GB of disk, and an IP address on the network card. Have them written down somewhere if needed.

7) Snapshot:

What is snapshot? it is a save. You can load if case something goes wrong.

In the VM: sudo poweroff. A snapshot of a switched-off VM is smaller and faster.

Take the snapshot:

select the VM → the menu icon next to its name → Snapshots → Take. Name it simple but coherent.

Congratulations! now you have your own VM with a Linux (ubuntu) on it.

**WINDOWS INSTALLATION**

Now we begin the process of instalation of Windows 11 VM.

CHECK YOUR SETTINGS! ENSURE THAT YOU HAVE ENOUGHT MEMORY AND SPACE FOR NEXT VM.

vCPU: 2 — Enough; never more than half your host's cores.

Memory: 4 GB (4096 MB) — Windows 11's minimum.

Disk: 64 GB, thin (dynamically allocated) — Windows 11's minimum; the file starts small.

Firmware: UEFI + Secure Boot — Required by Windows 11.

TPM: a virtual TPM 2.0 — Required by Windows 11.

1) Create the Windows VM:

Machine → New. Name YourName-windows, ISO Image: the Windows ISO, Type Microsoft Windows, Version Windows 11 (64-bit).

Tick Skip Unattended Installation.

Base Memory 4096 MB, Processors 2. Choosing the Windows 11 version turns on EFI, Secure Boot and TPM 2.0 for you.

Hard disk: Create a virtual hard disk now, 64 GB, Pre-allocate Full Size unticked.

Finish. Check Settings → System: Enable EFI ticked, TPM Version v2.0, Enable Secure Boot ticked.

2) Install Windows VM:

Start the VM. When you see "Press any key to boot from CD or DVD…", click inside the window and press a key quickly. Missed it? Restart the VM and try again.

Language, time format, keyboard: your choice → Next → Install now.

If asked for a product key: I don't have a product key. Edition: Windows 11 Enterprise (Evaluation).

Accept the licence terms → Custom: Install Windows only → select Drive 0 Unallocated Space → Next. Windows copies files and restarts several times. Do not press a key at the "boot from CD" prompt again.

Setup screens: country, keyboard, skip the second keyboard.

Account: on the sign-in screen choose Sign-in options → Domain join instead, then create a local account (name, password, three security questions). Write the password on paper, not in your repository. If your build does not offer Domain join instead, sign in with any Microsoft account, for example a free one you create for this course.

Privacy settings: switch everything off → Accept.

When the desktop appears, install the guest tools:

VMware: VM → Install VMware Tools. In Windows, open File Explorer → the DVD drive → run setup64.exe (or setup.exe) → Typical → restart.

VirtualBox: Devices → Insert Guest Additions CD image. In Windows, open the DVD drive → run VBoxWindowsAdditions.exe → defaults → restart.

After the restart, the screen fits the window and copy-paste between host and guest works — you will need it in step 5.

3) Network:

The brief asks for two things at once: the guests reach each other and the internet. Find your row and set both VMs the same way.

Why not plain "NAT" in VirtualBox? It gives each VM its own private router, so the two guests cannot see each other.

Why not bridged? At home it may work. On the campus Wi-Fi, unknown MAC addresses are often dropped and the guest gets no address. If you try bridged and it fails, write that in "What did not work the first time" — the brief says that observation counts.

Why not host-only? No internet, and the lab needs both.

First create one: File → Tools → Network Manager → NAT Networks → Create. Then each VM: Settings → Network → Adapter 1 → Attached to: NAT Network, the same name for both.

4) Check the network:

Now we need to check if both VMs can connect to the internet and to each other.

Start both VMs.

On Ubuntu, open the terminal and run:

ip -br a

ping -c 4 8.8.8.8

ping -c 4 ubuntu.com

On Windows, open Command Prompt and run:

ipconfig

ping 8.8.8.8

ping ubuntu.com

If you get replies, the internet connection works.

Now we need to check if the VMs can see each other. Find the IP address of each VM using ip -br a on Ubuntu and ipconfig on Windows.

From Ubuntu, run:

ping -c 4 <WINDOWS_IP>

From Windows, run:

ping <UBUNTU_IP>

Replace the IPs with the actual addresses of your VMs.

If Windows does not respond, its firewall might be blocking ping. This does not always mean that the network is broken.

5) Check the system information:

We already did this for Ubuntu, but let's make sure everything is working correctly.

On Ubuntu, run:

lsb_release -a

hostname

nproc

free -h

df -h /

ip -br a

On Windows, open Command Prompt and run:

systeminfo

hostname

ipconfig

Check the operating system, hostname, CPU, memory, disk space and IP address. Write down the results for your report.

6) Take snapshots:

Snapshots are useful when something goes wrong. Instead of installing everything again, you can return to a previous state.

Shut down Ubuntu:

sudo poweroff

Shut down Windows normally using Start → Power → Shut down.

In VirtualBox, select the VM, open Snapshots and click Take. Give each snapshot a name, for example ubuntu-initial-setup and windows-initial-setup.

Now you have a clean starting point for both machines.

7) Document your results:

Write down the configuration of both VMs.

| Parameter | Ubuntu | Windows |
|---|---|---|
| OS | Ubuntu Server | Windows 11 |
| CPU | 2 vCPUs | 2 vCPUs |
| RAM | 2 GB | 4 GB |
| Disk | 25 GB | 64 GB |
| Network | NAT Network | NAT Network |
| IP address | Your actual IP | Your actual IP |
| Snapshot | ubuntu-initial-setup | windows-initial-setup |

Use the actual values from your machines if they are different.

8) What if something doesn't work?

**No internet:** Check that the VM is connected to the correct NAT Network.

**VMs cannot connect to each other:** Make sure both use the same NAT Network. Also check the firewall settings.

**VM is slow:** Check how much RAM and CPU your host has available. Do not give the VMs too many resources.

**VM won't start:** Check your virtualization settings and make sure you have enough free disk space and memory.

**Wrong screen resolution:** Check that Guest Additions or VMware Tools are installed and restart the VM.

If you encounter a problem, write down what happened and what you tried to fix it. This will be useful for your report.

9) Final check:

Before finishing, make sure that:

- Ubuntu Server is installed and working.
- Windows 11 is installed and working.
- Guest Additions or VMware Tools are installed.
- Both VMs use the same NAT Network.
- Both VMs have internet access.
- Both VMs can communicate with each other.
- You have recorded the system information.
- You have taken snapshots of both VMs.
- Your passwords are not stored in the repository.

Congratulations! You now have two virtual machines ready for testing. You can experiment with Linux and Windows without making changes to your main system.

Remember to take snapshots before making major changes. It can save you a lot of time if something breaks.

Hope this wont make you feel confused and your first day will go easy. Have a great day. Bye bye 

(No AI was used)