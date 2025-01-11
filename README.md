# Analyzing Linux Rootkits

## Overview

This project documents hands-on research and analysis of Linux rootkits. It explores how rootkits compromise system security, provides step-by-step detection methods using tools like `chkrootkit`, and shares real-world observations from testing.

## Objectives

- Research Linux Rootkit 5 (LRK5) and its behavior.
- Use rootkit detection tools to analyze system integrity.
- Document findings and mitigation strategies for securing Linux systems.

---

## Key Topics

- **Linux Rootkits:** Malicious software that hides unauthorized access and manipulates system behavior.
- **Trojaned Commands:** Commands altered by rootkits to mask activities.
- **Detection Techniques:** Practical application of `chkrootkit` to uncover rootkits.
- **Analysis Results:** Observations from detection experiments.

---

## Steps and Findings

### 1. **Researching Linux Rootkit 5**
   - **Trojaned Commands Identified:**
     - `ls`: Hides malicious files from directory listings.
     - `ps`: Suppresses malicious processes from process lists.
     - `netstat`: Masks unauthorized network connections.
     - `ifconfig`: Conceals malicious network activity.
     - `login`: Enables backdoor user logins.

---

### 2. **Running `chkrootkit`**
   - **Installation:**
     ```bash
     sudo apt update
     sudo apt-get install chkrootkit
     ```
   - **Execution:**
     ```bash
     sudo chkrootkit
     ```
   - **Results:**
     - No infections found for `ls`, `ps`, `netstat`, `ifconfig`, or `login`.
     - Warnings included:
       - **Packet Sniffer:** Likely triggered by Wireshark in promiscuous mode.
       - **`wted` Log Warning:** Potential hidden processes or tampered logs.
       - **Deleted Logs (`chkwtmp`):** Indicated two deletions between October 6, 06:55:50, and 06:57:12. Confirmed as user-initiated.

---

### 3. **Understanding Findings**
   - **Packet Sniffer Warning:** A benign false positive due to Wireshark capturing network traffic.
   - **Log Tampering (`wted`):** Although flagged, further verification confirmed no malicious activity.
   - **Deleted Logs:** Detected changes aligned with legitimate user actions, demonstrating `chkrootkit`'s ability to flag all log alterations.

---

### 4. **Outcomes**
   - Rootkits were not detected, but warnings highlighted areas for further verification.
   - The experiment demonstrated how tools like `chkrootkit` effectively scan for malicious activity and identify potential threats.

---

## Tools and Resources

- **Tools Used:**
  - `chkrootkit`: A Linux rootkit scanner.
  - Wireshark: For network analysis and troubleshooting.
- **References:**
- [Linux Security Modules](https://www.kernel.org/doc/html/latest/admin-guide/LSM/index.html)
- [Rootkit Hunter](http://rkhunter.sourceforge.net/)
- [Chkrootkit](http://www.chkrootkit.org/)
- [Packet Storm Security](https://packetstormsecurity.org)

---

## Deliverables

- Practical analysis of Linux Rootkit 5 and its impact.
- Documented use of `chkrootkit` for detection and analysis.
- Recommendations for maintaining system integrity and mitigating rootkit threats.

---

## Important Notes

- Regularly update detection tools and monitor flagged activities.
- Cross-check warnings, as tools like `chkrootkit` can produce false positives (e.g., Wireshark in promiscuous mode).
- Investigate flagged log changes to ensure system integrity.

---

## Author

**Stephanie Vergil**

This repository captures hands-on work and analysis, providing a guide for detecting and mitigating Linux rootkits. For a detailed report, refer to the [full document](https://github.com/StephVergil/Analyzing-Linux-Rootkits/blob/main/Homework%208%20Linux%20Rootkits.docx).
