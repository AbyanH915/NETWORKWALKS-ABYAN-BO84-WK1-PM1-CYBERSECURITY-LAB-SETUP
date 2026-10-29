# CYBERSECURITY-LAB-WK-1-BO84
Cybersecurity Lab Setup WK1 - BO84 | Parrot OS + VirtualBox + Kali Linux 2026.2 | NAT Network 10.0.0.0/24
# Cybersecurity Lab Setup - Week 1 | BO84

A hands-on project documenting the creation of a virtual cybersecurity lab using Parrot OS, VirtualBox, and Kali Linux for learning network configuration and security testing.

## 📌 1. Project Overview
This project focuses on building a controlled cybersecurity lab using Parrot OS as host. The goal is to prepare a reliable environment where security tools can be explored and network behavior can be observed safely.

## 🎯 2. Objectives
- Install and configure Oracle VirtualBox on Parrot OS
- Setup Kali Linux as cybersecurity workstation
- Create dedicated NAT Network
- Understand IP, Subnet, Gateway, DNS
- Verify connectivity using Linux commands
- Create recoverable snapshot

## 🧰 3. Tools
- Parrot OS (host)
- Oracle VirtualBox v7.x
- Kali Linux 2026.2
- Nmap
- GitHub

## 🏗️ 4. Lab Design
HOST (Parrot OS) -> VirtualBox -> NAT Network LabNAT1 (10.0.0.0/24) -> Kali Linux (10.0.0.2)

## ⚙️ 5. My Configuration
- Host OS: Parrot OS
- Host RAM: 8GB
- VirtualBox: v7.x
- Kali Version: 2026.2
- Kali RAM: 2GB
- Network Mode: NAT Network
- Network Name: LabNAT1
- IPv4 Network: 10.0.0.0/24
- Kali IP: 10.0.0.2
- Gateway: 10.0.0.1
- DNS: 8.8.8.8
- Snapshot: cyberLab1
- Shared Folder: sf_Downloads

## 🪜 6. Implementation Steps
### Step 1: Host Preparation
Checked virtualization support on Parrot OS, installed VirtualBox.

### Step 2: Install VirtualBox
Installed VirtualBox on Parrot OS and verified.

### Step 3: Setup Kali
Imported Kali .vdi, allocated 2GB RAM, configured network adapter to NAT Network.

### Step 4: Configure Network
Created NAT Network LabNAT1 10.0.0.0/24 with DHCP enabled.
Attached Kali adapter to LabNAT1.

### Step 5: Inspect Network
Commands used:

ip a
ip route


### Step 6: Verify Connectivity

ping -c 4 10.0.0.1
ping -c 4 8.8.8.8
getent hosts example.com
nmap --version


### Step 7: Snapshot
Created snapshot `cyberLab1` for recovery.

## 🔎 7. Results
| Test | Command | Result |
|------|---------|--------|
| IP Assignment | ip a | PASS - 10.0.0.2/24 |
| Routing | ip route | PASS - default via 10.0.0.1 |
| Gateway | ping 10.0.0.1 | PASS |
| External | ping 8.8.8.8 | PASS |
| DNS | getent hosts | PASS |
| Nmap | nmap --version | PASS |
| Snapshot | VirtualBox Manager | PASS |

Overall: Completed

## 🐛 8. Challenges
**Challenge: No IPv4 Address**
Observed: eth0 only showed inet6, no inet.
Investigation: Checked `ip a` - DHCP didn't assign IP.
Solution: Manually set IP with:

sudo ip addr add 10.0.0.2/24 dev eth0
sudo ip route add default via 10.0.0.1
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf

**Challenge: Small Screen / Black Borders**
Solution: Installed Guest Additions:

sudo apt update && sudo apt install -y virtualbox-guest-x11
sudo reboot


## 🧠 9. Lessons Learned
- How NAT Network works
- Using `ip a` and `ip route` to troubleshoot
- Importance of snapshots
- Guest Additions for display and shared folders
<img width="1600" height="900" alt="WhatsApp Image 2026-10-29 at 10 44 11 AM" src="https://github.com/user-attachments/assets/7ca69ad8-269f-4b29-91e0-8cfbf5b87a39" />
<img width="900" height="1600" alt="WhatsApp Image 2026-10-29 at 10 24 42 AM" src="https://github.com/user-attachments/assets/a0c48168-8251-4056-a455-8492b70c682b" />
<img width="900" height="1600" alt="WhatsApp Image 2026-10-29 at 9 35 39 AM" src="https://github.com/user-attachments/assets/f950b7d8-76b1-4902-95dd-6879a2b0fa90" />
