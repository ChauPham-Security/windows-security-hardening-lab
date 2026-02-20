# STIG Remediation — WN10-AU-000582  
**Microsoft Windows 10 STIG V3R1**

---

## Overview

This control ensures that successful file system access events are audited to provide visibility into file and folder activity.

**STIG Requirement**

> The system must audit File System successes.

---

## What This Means (Simple Explanation)

The File System audit policy allows Windows to log when users or processes successfully access files and folders.

This setting enables the capability to record successful file access events.

Note: Object-level auditing must also be configured on specific files or directories for events to generate.

---

## Why This Matters

Auditing successful file access helps detect:

- Unauthorized data access  
- Insider threat behavior  
- Sensitive file browsing  
- Potential data exfiltration  

This strengthens visibility into file system activity and supports incident investigations.

---

## Technical Details

- **STIG ID:** WN10-AU-000582  
- **Audit Policy Subcategory:** `File System`  
- **Required Setting:** Success enabled  
- **Configuration Tool:** `auditpol`

---

## Remediation Script

```powershell
<#
.SYNOPSIS
    Enables auditing for File System (Success)
    to meet STIG WN10-AU-000582.

.NOTES
    Author          : Chau Pham
    Date Created    : 2026-02-20
    Version         : 1.0
    STIG-ID         : WN10-AU-000582

.USAGE
    Run as Administrator:
    PS C:\> .\remediate-WN10-AU-000582.ps1
#>

$subcategory = "File System"

try {
    Write-Output "Enabling Success auditing for '$subcategory'..."

    # Enable Success auditing
    auditpol /set /subcategory:"$subcategory" /success:enable | Out-Null

    # Verify configuration
    $result = auditpol /get /subcategory:"$subcategory"

    Write-Output "Verification Output:"
    Write-Output $result

    if ($result -match "Success") {
        Write-Output "SUCCESS: Success auditing is enabled for '$subcategory'."
        exit 0
    }
    else {
        Write-Output "ERROR: Success auditing is NOT enabled for '$subcategory'."
        exit 1
    }
}
catch {
    Write-Output "ERROR: $($_.Exception.Message)"
    exit 1
}
