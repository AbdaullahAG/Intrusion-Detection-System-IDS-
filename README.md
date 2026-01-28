# Network Intrusion Protection: IDS
## Executive Summary

This project demonstrates the successful implementation of an **Intrusion Detection System (IDS)** using **Snort 3** on **Kali Linux** in a virtualized environment.

Key features implemented:
- Real-time network traffic inspection
- Creation of custom detection rules
- Threat detection and logging

The system was tested against various attack vectors including:
- ICMP ping floods
- TCP SYN port scans
- Nmap OS detection
- SSH/Telnet brute-force attempts
- HTTP traffic enumeration

All major threats were successfully detected and logged.

This phase establishes a solid foundation for transitioning to **Intrusion Prevention System (IPS)** mode in future work.

## Technologies Used
- **OS:** Kali Linux (Virtualized – Oracle VirtualBox recommended)
- **IDS Tool:** Snort 3
- **Testing Tools:** Nmap, hping3, ssh/telnet clients, web browser
- **Interface:** eth0 (bridged or internal network in VM)

## Setup & Configuration Commands

```bash
# Test Snort configuration
sudo snort -c /etc/snort/snort.lua -T

# Run Snort in IDS mode (passive monitoring with fast alerts)
sudo snort -c /etc/snort/snort.lua -i eth0 -A alert_fast
Alerts are logged to /var/log/snort/alert_fast.txt by default.
Detection Rules Overview
Snort rules follow this syntax:
textalert protocol src_ip src_port -> dst_ip dst_port (msg:"Description"; sid:unique_id; rev:version; content:"pattern";)
Key components:

alert → Action (alert / drop / reject)
protocol → TCP, UDP, ICMP, IP
src_ip/src_port → Source (use any for all)
dst_ip/dst_port → Destination
msg → Alert message
sid → Unique rule ID

Custom rules were created for the following attack types (SID range: 1000001–1000007).
Detection Summary
Attack TypeRule SIDDetection StatusAlerts GeneratedICMP Ping Flood1000001✓ Detected+20 alertsTCP SYN Scan1000002✓ Detected~1000 alertsNmap OS Detection1000003✓ DetectedMultiple alertsSSH Attempt1000005✓ DetectedMultiple attemptsTelnet Attempt1000006PARTIALConnection refusedHTTP Traffic1000007PARTIALWeb requests logged
Screenshots
Snort Configuration Test & IDS Run
Snort Config Test
Snort IDS Running
ICMP Ping Flood Detection
ICMP Alerts
TCP SYN Scan & Nmap Detection
SYN Scan Alerts
Nmap OS Detection
SSH & Telnet Attempts
SSH Telnet Alerts
HTTP Traffic Monitoring
HTTP Alerts
(All screenshots are included in the /screenshots folder)
Key Achievements

✓ Installed and configured Snort 3 in passive IDS mode
✓ Created custom detection rules for 5+ attack types
✓ Successfully detected and logged all major test attacks
✓ Generated comprehensive alert logs
✓ Identified and resolved configuration challenges
✓ Established foundation for IPS implementation (active blocking)

Conclusion
This project successfully demonstrated the implementation and effectiveness of Snort 3 as an IDS. The system reliably detected network reconnaissance, port scanning, and service enumeration attempts, providing valuable hands-on experience with real-world network security tools.

Note: For best viewing, open screenshots in full size. If you replicate this project, ensure proper network isolation in a lab environment.
text
