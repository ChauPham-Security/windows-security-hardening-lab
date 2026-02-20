# STIG Remediation — WN10-AU-000115  
**Microsoft Windows 10 STIG V3R1**

---

## Overview

This control enables auditing of **Sensitive Privilege Use (Success)** events to ensure the system records when high-impact privileges are successfully exercised.

**STIG Requirement**

> The system must be configured to audit Sensitive Privilege Use – Success.

---

## Why This Matters

Sensitive privileges allow powerful actions such as:

- Debugging system processes  
- Acting as part of the operating system  
- Loading drivers  
- Impersonating other users  
- Managing system security  

If an attacker gains administrative access, these privileges are often used during post-exploitation.

Auditing successful privilege use provides:

- Visibility into administrative activity  
- Detection of privilege abuse  
- Forensic evidence during investigations  
- Stronger compliance posture  

---

## Technical Details

- **STIG ID:** WN10-AU-000115  
- **Audit Policy Subcategory:** `Sensitive Privilege Use`  
- **Required Setting:** `Success` enabled  

---

## Remediation Script

```powershell
<#
.SYNOPSIS
    Enables auditing for Sensitive Privilege Use (Success)
    to meet STIG WN10-AU-000115.

.NOTES
    Author          : Chau Pham
    Date Created    : 2026-02-20
    Version         : 1.0
    STIG-ID         : WN10-AU-000115

.USAGE
    Run as Administrator:
    PS C:\> .\remediate-WN10-AU-000115-SensitivePrivilegeUseSuccess.ps1
#>

$subcategory = "Sensitive Privilege Use"

try {
    Write-Output "Configuring audit policy for '$subcategory' (Success only)..."

    # Enable Success auditing
    auditpol /set /subcategory:"$subcategory" /success:enable | Out-Null

    # Retrieve current setting in consistent format
    $result = auditpol /get /subcategory:"$subcategory" /r
    Write-Output "Verification Output:"
    Write-Output $result

    # Validate Success is enabled
    if ($result -match "Success") {
        Write-Output "SUCCESS: '$subcategory' auditing is enabled for Success."
        exit 0
    }
    else {
        Write-Output "ERROR: '$subcategory' auditing is NOT enabled for Success."
        exit 1
    }
}
catch {
    Write-Output "ERROR: $($_.Exception.Message)"
    exit 1
}
