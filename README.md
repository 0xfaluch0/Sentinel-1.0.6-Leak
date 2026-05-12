# Sentinel 1.0.6 RAT - Malware Analysis & Research

> ⚠️ ⚠️ ⚠️**WARNING:** This repository contains LIVE MALWARE source files, builders, and uncompiled payloads. ⚠️**I HAVEN'T CHECKED IF IT HAS A HIDDEN BACKDOOR OR SOMETHING LIKE THAT**. It is strictly for educational purposes, malware analysis, and Threat Intelligence research. Do NOT execute any of these files on your host operating system. The author is not responsible for any misuse.

##  Overview
This repository contains the extracted server and builder components of a .NET-based Remote Access Trojan (RAT) dubbed **"Sentinel"**. 
In this video is explained how is was "Taken" -> [to be uploaded] and is being shared to help the cybersecurity community analyze its capabilities.

Based on the directory structure, this is NOT the client payload, but the **Attacker's Control Panel and Payload Builder**.

##  Architecture Breakdown
The toolkit is highly modular, relying on dynamic DLL loading.

### 1. The Server (`/Server`)
The core listening post and control panel for the attacker. 
* `SentinelStandaloneServer.dll` / `.exe`: The main executable for the C2 panel.
* Requires manual port and password configuration via `StartLinux.sh` or `StartWindows.bat` to accept incoming reverse connections from infected hosts.
* Password is -> Pa55w0rd

### 2. The Plugins (`/Plugins`)
The RAT features plugin ecosystem, pushed to the victim's machine in-memory to execute specific tasks:
* **Surveillance:** `HiddenVNC.dll`, `RemoteWebcam.dll`, `RemoteAudio.dll`, `Keylogger.dll`.
* **System Control:** `RemoteShell.dll`, `Taskmanager.dll`, `FileManager.dll`.
* **Credential Theft:** Specific modules targeting gaming accounts (`Steam Token Loginer`).
* **Evasion & Privilege:** `ElevatePrivileges.dll`, `BouncyCastle.Cryptography.dll` (likely for traffic encryption and obfuscation).


---
*Analyzed and shared for the Infosec community.*
