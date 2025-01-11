# Analyzing Linux Rootkits

## Overview

This project demonstrates techniques to detect and analyze Linux rootkits. By using practical tools and resources, the project explores how rootkits compromise system security and the methods to identify and mitigate their impacts.

## Objectives

- Research common Linux rootkits and their behavior.
- Utilize rootkit-checking tools for detection and analysis.
- Document findings and recommendations for securing Linux systems.

## Key Topics

- **Linux Rootkits:** Overview of how they operate and compromise systems.
- **Trojaned Commands:** Identifying Linux commands altered by rootkits, such as `ls`, `ps`, `ifconfig`, `netstat`, and `login`.
- **Detection Techniques:** Utilizing tools like `chkrootkit` to uncover malicious activity.

## Steps Undertaken

1. **Rootkit Identification:**
   - Explored [Packet Storm Security](https://packetstormsecurity.org) to research Linux Rootkit 5 (LRK5).
   - Identified five commonly Trojaned Linux commands: `ls`, `ps`, `netstat`, `ifconfig`, and `login`.

2. **Rootkit Detection:**
   - Installed and ran the `chkrootkit` tool using the following commands:
     ```bash
     sudo apt update
     sudo apt-get install chkrootkit
     sudo chkrootkit
     ```
   - Analyzed the scan results for signs of rootkits or other malicious activities.

3. **Analyzing Findings:**
   - Verified system integrity by reviewing flagged warnings (e.g., suspicious files, packet sniffers, and log tampering).
   - Identified benign warnings, such as those caused by Wireshark in promiscuous mode.
   - Investigated flagged deletions in system logs to confirm their legitimacy.

4. **Learning Outcomes:**
   - Recognized how `chkrootkit` scans for malicious replacements of system files.
   - Understood the importance of verifying warnings to differentiate between normal and suspicious activities.

## Tools and Resources

- **Tools:** 
  - `chkrootkit`: A Linux rootkit scanner.
  - Wireshark: For network analysis and troubleshooting.
- **Resources:** 
  - [Packet Storm Security](https://packetstormsecurity.org) for rootkit samples.
  - Documentation on Linux security best practices.

## Deliverables

- **Documentation:**
  - Detailed analysis of Linux Rootkit 5.
  - Findings on Trojaned Linux commands and mitigation strategies.
  - Recommendations for securing systems against rootkits.
- **Practical Steps:**
  - Scripts and tools to detect and analyze rootkits.
  - Comparison of clean and compromised system states.

## Important Notes

- The `chkrootkit` tool is a powerful scanner but may produce warnings for benign activities. For example, Wireshark's promiscuous mode can trigger false positives for packet sniffers.
- Investigate all flagged warnings, such as deletions in system logs or suspicious files, to confirm whether they are threats or legitimate activities.
- Regular monitoring and timely patching are critical for maintaining system security.

## References

- [Linux Security Modules](https://www.kernel.org/doc/html/latest/admin-guide/LSM/index.html)
- [Rootkit Hunter](http://rkhunter.sourceforge.net/)
- [Chkrootkit](http://www.chkrootkit.org/)
- [Packet Storm Security](https://packetstormsecurity.org)

## Author

**Stephanie Vergil**

This repository offers practical exercises, detailed analyses, and resources to understand, detect, and mitigate Linux rootkits effectively. Explore the project for actionable insights into securing Linux systems.
