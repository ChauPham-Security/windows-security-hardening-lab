# windows-security-hardening-lab

# Windows Security Hardening & Vulnerability Remediation Lab

## Objective
This repository demonstrates a structured security improvement workflow on a Windows 10 VM by completing:

- **Program 1:** Remediate and automate **10 DISA Windows 10 STIG V3R1** controls
- **Program 2:** Remediate and validate **10 vulnerability findings** identified through scanning

The goal is to simulate an enterprise-style remediation lifecycle (baseline → fix → validate → document → automate), not isolated lab tweaks.

---

## Environment
- **Target:** Azure Windows 10 Virtual Machine
- **Scanning:** Tenable.io (Compliance + Vulnerability scanning)
- **STIG Standard:** **Microsoft Windows 10 STIG V3R1**
- **Automation:** PowerShell (native on Windows 10)
