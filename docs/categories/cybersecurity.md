# Cybersecurity

Python is a powerful language for cybersecurity professionals due to its simplicity, wide array of libraries, and capabilities for automation, scanning, and exploit development. It’s widely used in penetration testing, malware analysis, and network security.

## 🔐 Key Applications

- **Penetration Testing**: Automating vulnerability scans and exploiting known flaws.
- **Network Scanning & Analysis**: Detecting open ports, services, and sniffing traffic.
- **Web Application Testing**: Fuzzing inputs, testing endpoints, simulating attacks.
- **Malware Analysis**: Reverse engineering and analyzing malicious payloads.
- **Cryptography**: Implementing encryption, decryption, and secure data handling.
- **Forensics**: Parsing log files, recovering deleted data, or analyzing file metadata.

## 🛠️ Common Libraries & Tools

| Library/Tool   | Purpose                                          |
| -------------- | ------------------------------------------------ |
| `scapy`        | Packet crafting, sniffing, and network tools     |
| `socket`       | Low-level networking operations                  |
| `nmap`         | Network mapping and scanning (via `python-nmap`) |
| `requests`     | Interact with HTTP for web-based testing         |
| `paramiko`     | SSH connectivity and command execution           |
| `cryptography` | Modern encryption and cryptographic operations   |
| `hashlib`      | Hash functions (SHA256, MD5, etc.)               |
| `pyshark`      | Python wrapper for Wireshark’s tshark            |
| `pwntools`     | CTF (Capture The Flag) and exploit development   |

## 🧪 Example Use Cases

- Scan a subnet and detect live hosts using `scapy` or `nmap`
- Automate brute force login testing on web forms
- Create a simple port scanner using raw sockets
- Write a script to sniff and log DNS traffic
- Encrypt/decrypt files or passwords securely
- Build tools for CTF (Capture The Flag) competitions

## 🧱 Sample Code: Basic Port Scanner

```python
import socket

target = "192.168.1.1"
ports = [21, 22, 80, 443]

for port in ports:
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    s.settimeout(1)
    result = s.connect_ex((target, port))
    if result == 0:
        print(f"Port {port} is open")
    s.close()
```

---

## ⚠️ Ethical Use Reminder

> Always use your tools and scripts **legally** and **ethically**. Obtain **explicit permission** before scanning or testing any systems.

---

## 📚 Learning Resources

- [Python for Pentesters (book)](https://www.packtpub.com/product/python-for-penetration-testers/9781788995238)
- [Scapy Documentation](https://scapy.readthedocs.io/)
- [Nmap + Python](https://xael.org/pages/python-nmap-en.html)
- [Cryptography Library](https://cryptography.io/en/latest/)
- [Hack The Box](https://www.hackthebox.com/)
- [TryHackMe](https://tryhackme.com/)

---

> **Tip**: Python scripts can quickly automate reconnaissance, exploit development, and post-exploitation — making it a favorite among ethical hackers and red teams.
