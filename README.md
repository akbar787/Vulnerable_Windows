__Overview__

This setup.bat script is part of a Local Privilege Escalation (LPE) workshop, originally created by Sagi Shahar (@s4gi_) and Tib3rius (@tibsec). It intentionally introduces multiple security misconfigurations in a freshly installed Windows 10 machine, allowing for exploitation in a controlled environment.

The goal is to simulate real-world security flaws for penetration testers, ethical hackers, and security researchers.

**What This Script Does**
This script sets up a Windows machine with various local privilege escalation (LPE) vulnerabilities, including:

**1️⃣ Unquoted Service Paths**
Creates a vulnerable Windows service with an unquoted executable path.

Allows attackers to hijack execution by placing malicious executables in directories with spaces.

**2️⃣ Weak File and Folder Permissions**
Modifies ACLs (Access Control Lists) to allow Authenticated Users to modify system files.

Attackers can replace system files with malicious payloads for privilege escalation.

**3️⃣ Weak Registry Key Permissions**
Grants full control to Authenticated Users on specific registry keys.

Attackers can modify service configurations to execute arbitrary code.

**4️⃣ Stored Credentials in Plaintext**
Creates a user account with a weak password.

Stores credentials in plaintext locations that tools like mimikatz can retrieve.

**5️⃣ Enables SMBv1 (Legacy and Insecure Protocol)**
Re-enables SMBv1, making the system vulnerable to exploits like EternalBlue.

Allows lateral movement and remote code execution (RCE).

**6️⃣ Disables Windows Defender and Security Features**
Turns off Windows Defender’s real-time protection.

Disables User Account Control (UAC) to allow scripts to run without admin prompts.

**7️⃣ Creates Insecure Scheduled Tasks**
Configures a scheduled task to run as SYSTEM using a user-modifiable script.

Can be exploited to execute arbitrary code with SYSTEM privileges.

**8️⃣ Weak Network Share Permissions**
Shares system folders with Everyone: Full Control permissions.

Attackers can upload or modify files remotely.

**How to Use**
1️⃣ Run the Script

Ensure you are using an isolated virtual machine. Then, execute the script as an administrator:

`setup.bat`

**2️⃣ Verify Misconfigurations**
Use PowerShell to check for vulnerabilities:

Invoke-AllChecks

**3️⃣ Exploit the Vulnerabilities**
Use tools like:

`Metasploit`

`PowerUp.ps1`

`mimikatz1

`crackmapexec`

**Remediation**

To harden the system after testing, follow these steps:

Re-enable security settings (Windows Defender, UAC, SMBv2).

Restrict file and registry permissions using Group Policy or PowerShell.

Remove unquoted service paths and reconfigure services securely.

Disable unnecessary network shares.

**Disclaimer**
This script is for educational and security research purposes only. Do not use it on unauthorized systems. The author is not responsible for any misuse or damage caused by this script.

**Next Steps**
Test privilege escalation using PowerUp.ps1 as show in the document.

Attempt local and remote exploitation scenarios.

Reverse the misconfigurations to understand system hardening techniques.
