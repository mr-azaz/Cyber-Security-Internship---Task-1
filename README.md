# Cyber-Security-Internship---Task-1
# 🔐 Task 1: Scan Your Local Network for Open Ports

## 🎯 Objective
The purpose of this task is to discover open ports on devices within the local network using **Nmap**, and analyze the resulting traffic with **Wireshark** to understand how scanning appears at the packet level.

---

## 🛠 Tools Used
- **Nmap**: For port scanning and host discovery  
- **Wireshark**: For capturing and analyzing network traffic

---

## 🌐 IP Range Scanned
192.168.220.1
192.168.220.7
192.168.220.8
192.168.220.10
192.168.220.11
---

## 📊 Nmap Scan Summary

Nmap was used to perform a **TCP SYN scan** across the local subnet. The following open ports and services were discovered:

| IP Address      | Port | Protocol | State | Service       | Version/Details      |
|------------------|------|----------|--------|----------------|-----------------------|
| 192.168.220.1    | 53   | TCP      | Open   | domain         | dnsmasq 2.80          |
| 192.168.220.1    | 80   | TCP      | Open   | tcpwrapped     |                       |
| 192.168.220.1    | 443  | TCP      | Open   | ssl/tcpwrapped |                       |

> Output saved in: `task1_scan_result.txt`

> Other ip scans are closed/blocked by Firewall.
---

## 📦 Wireshark Packet Analysis

Wireshark was used to capture traffic during the Nmap scan and identify how open and closed ports respond.

### ✅ Filters Applied:
| Filter | Purpose |
|--------|---------|
| `ip.addr == 192.168.220.1` | Focus on traffic involving the target host |
| `tcp.flags.syn == 1 && tcp.flags.ack == 0` | Show SYN packets sent by Nmap |
| `tcp.flags.syn == 1 && tcp.flags.ack == 1` | Show SYN-ACK replies (indicates open ports) |
| `tcp.flags.reset == 1` | Show reset packets (indicates closed ports) |
| `tcp.flags.syn == 1` | Show both SYN and SYN-ACK packets |
| `tcp` | Display all TCP traffic |
| `udp` | Display all UDP traffic |

> Packet capture saved as: `task1-wireshark.pcapng`

---

## 🧠 Key Observations
- Port **53** was open and running **dnsmasq 2.80**, which typically provides DNS and DHCP services.
- Port **80** and **443** were detected as open but **tcpwrapped**, which means Nmap couldn’t determine the exact service due to access control (likely due to a firewall or security feature).
- Wireshark confirmed SYN and SYN-ACK exchanges for open ports, and no RST packets were seen for these services, confirming their availability.

---

## 📁 Files Included

| File | Description |
|------|-------------|
| `task1_scan_result.txt` | Nmap scan result output |
| `task1-wireshark.pcapng` | Wireshark packet capture |
| `screenshots/` |

---

## 🚀 Conclusion
This task helped understand how attackers or administrators can map out exposed services on a local network. The combination of **Nmap scanning** and **Wireshark inspection** provided both high-level visibility and low-level packet insight.

---

## 📌 Next Steps
- Use `nmap -sV` to get more detailed version info
- Try scanning with `-A` or `-O` options for OS and service detection
- Explore how firewalls block or filter Nmap probes

---

#cybersecurity #nmap #wireshark #internship #networksecurity #task1

