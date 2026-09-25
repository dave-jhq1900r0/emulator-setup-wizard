# emulator-setup-wizard

This is my personal utility to bootstrap and maintain emulation environments on Windows. I got tired of manually mapping directories, copying massive BIOS files across drives, and re-configuring RetroArch hotkeys and directories every time I reinstalled Windows or set up a new handheld/mini-PC.

It performs three main tasks:
1. **Audits BIOS files**: Scans a directory and verifies MD5 checksums against known good dumps for PlayStation, Saturn, Dreamcast, and Game Boy Advance.
2. **Manages Directory Links**: Creates directory junctions to link your ROMs and BIOS folders from a central storage location (like a secondary SSD or network share) directly into RetroArch's folders.
3. **Patches RetroArch Config**: Safely updates `retroarch.cfg` line-by-line with optimal defaults (hotkeys, fast-forward, paths, saving behavior) without wiping out your existing controller mappings.

## Setup

No dependencies required. This script uses the Python standard library exclusively.

Clone this repository or just download `wizard.py` directly:

```powershell
curl -o wizard.py https://raw.githubusercontent.com/username/emulator-setup-wizard/main/wizard.py
```

## Usage

Run the script from a PowerShell or Command Prompt window.

### 1. Audit BIOS files
Check if your BIOS files are complete and match standard verified dumps:

```powershell
python wizard.py audit --bios "D:\Emulation\BIOS"
```

### 2. Link directories
Create directory junctions from your external/secondary drive to your local RetroArch installation:

```powershell
python wizard.py link --source "D:\Emulation" --retroarch "C:\Users\Alex\AppData\Roaming\RetroArch"
```

### 3. Patch RetroArch configuration
Apply sensible defaults (auto-save on exit, clean directories, fast-forward toggles) to your `retroarch.cfg` file:

```powershell
python wizard.py patch --config "C:\Users\Alex\AppData\Roaming\RetroArch\retroarch.cfg" --roms "D:\Emulation\ROMs" --bios "D:\Emulation\BIOS"
```

Use `--dry-run` with any command to see what changes would be made without writing anything to disk.

<!-- refreshed: 2026-09-25 -->
