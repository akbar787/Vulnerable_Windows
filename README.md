Windows 10 Misconfiguration Setup
Overview

This setup.bat script is designed to intentionally introduce multiple security misconfigurations in a freshly installed Windows 10 machine. These misconfigurations can be exploited for penetration testing, red teaming, or security research.

Features & Misconfigurations Introduced

1️⃣ Unquoted Service Paths

Creates a service with an unquoted executable path, making it vulnerable to privilege escalation.

Allows an attacker to place a malicious executable in a writable directory and gain SYSTEM privileges.

2️⃣ Weak File Permissions on Executables

Modifies ACLs (Access Control Lists) to allow Authenticated Users to modify critical executable files.

Allows privilege escalation by replacing the executable with a malicious payload.

3️⃣ Weak Registry Permissions

Grants full control to Authenticated Users on specific registry keys.

Enables attackers to modify service paths, allowing for persistence and privilege escalation.

4️⃣ Stored Credentials in Plaintext

Creates a user with a hardcoded weak password.

Stores credentials in plaintext files that can be retrieved using tools like mimikatz.

5️⃣ Enables SMBv1 (Insecure Protocol)

Enables SMBv1, which is vulnerable to exploits like EternalBlue.

Allows lateral movement and remote code execution (RCE).

6️⃣ Disables Windows Defender & Security Features

Disables Windows Defender real-time protection.

Turns off UAC (User Account Control) to allow execution of malicious scripts without prompts.

7️⃣ Adds Insecure Scheduled Tasks

Creates a scheduled task running as SYSTEM that executes a user-modifiable script.

Can be exploited for privilege escalation.

8️⃣ Weak Network Share Permissions

Shares folders with Everyone: Full Control permissions.

Allows attackers to upload or modify files remotely.
