# Nmap Network Scanning – Kali Linux

## Objective

The objective of this task is to perform a detailed network scan using **Nmap** on Kali Linux, identify all active hosts and their open ports within the local network, analyze traffic using **Wireshark**, research services running on discovered ports, and evaluate potential security risks.

---

## 🛠Tools Used

- 🐧 Kali Linux (Rolling)
- 🌐 Nmap 7.95
- 📡 Wireshark (for live packet capture)
- 📝 Terminal & bash scripting (CLI interface)

---

##  Step-by-Step Procedure

1. Find Local IP Range

Used `ip address show` to identify local IP and subnet:
```bash
ip address show
Output: inet 192.168.230.130/24 ...


 2. Run TCP SYN Scan
Scanned the local network for live hosts and open ports:

bash
Copy code
sudo nmap -sS 192.168.230.0/24
-sS: SYN scan (stealth scan)

Detected devices and open TCP ports

 3. Save Scan Results
Results saved to a file:

bash
Copy code
sudo nmap -sS 192.168.230.0/24 -oN scan_results.txt
 4. Analyze with Wireshark (Optional)
Started Wireshark:

bash
Copy code
wireshark &
Captured on interface eth0

Used display filter:

ini
Copy code
tcp.flags.syn == 1 and tcp.flags.ack == 0
This highlights initial TCP connection attempts (SYN scan).

📸 Screenshot saved as nmap_syn_packets.png

 5. Detect Services on Open Ports
Ran service detection to learn what's running on each port:

bash
Copy code
sudo nmap -sV 192.168.230.0/24
Example ports found:

22/tcp → SSH

80/tcp → HTTP

139/tcp, 445/tcp → SMB

 6. Check for Vulnerabilities
Used Nmap’s vulnerability detection scripts:

bash
Copy code
sudo nmap --script vuln 192.168.230.0/24
⚠️ Only used on local network (ethical testing only).

 7. Review & Research Open Ports
Used:

SpeedGuide

Nmap Port List

to understand service risks.

