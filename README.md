# 🖥️ Fixing INACCESSIBLE_BOOT_DEVICE (Windows BSOD Boot Error)

`INACCESSIBLE_BOOT_DEVICE` is a critical Windows Blue Screen (BSOD) error that occurs when the operating system cannot access the system boot drive. This commonly happens after hardware changes, BIOS misconfiguration, or corrupted boot files.

> ✅ **SEO Keywords**: Windows BSOD, INACCESSIBLE_BOOT_DEVICE, boot drive error, AHCI mode, RAID controller, boot configuration data, fix boot error, Windows 10 boot issue, storage drivers

---

## 🔍 Overview

This repository provides a complete guide to diagnose and fix the `INACCESSIBLE_BOOT_DEVICE` stop code (0x0000007B) on Windows 10/11. It includes step-by-step instructions, repair tools, BIOS settings, and disk recovery tips.

---

## 🛠️ Solutions

### 1. Repair Boot Configuration (MBR & BCD)
Use Windows Recovery or bootable USB:
```bash
bootrec /fixmbr
bootrec /fixboot
bootrec /scanos
bootrec /rebuildbcd
```
For UEFI systems:
```bash
bcdboot C:\Windows /s <EFI-partition> /f ALL
```

### 2. Check BIOS/UEFI Storage Settings
- Restart your PC and enter BIOS/UEFI (`Del`, `F2`, etc.)
- Go to **SATA Configuration** or **Storage Mode**
- Ensure mode matches your Windows installation (**AHCI** or **RAID**)
- Save and exit

### 3. Validate Boot Disk
```bash
diskpart
list disk
select disk 0
list volume
```
Make sure the OS volume is present and the disk is online.

### 4. Remove Problematic Updates or Drivers
From Windows Recovery:
- Troubleshoot → Advanced Options → Uninstall Updates
Or via terminal:
```bash
DISM /Image:C:\ /Get-Packages
DISM /Image:C:\ /Remove-Package /PackageName:<name>
```

### 5. Check File System and System Integrity
```bash
chkdsk C: /f /r
sfc /scannow
DISM /Online /Cleanup-Image /RestoreHealth
```

### 6. Disconnect New Hardware
- Unplug recent drives or USB storage devices
- Restore original drive configuration

### 7. Update Drivers and BIOS
- Boot into Safe Mode
- Download latest storage (AHCI/NVMe) drivers
- Update BIOS/UEFI firmware

### 8. System Restore or Windows Reset
Use System Restore to revert to a working configuration. If that fails:
- Use **Reset this PC** with “Keep my files” or do a clean install

### 9. Hardware Testing & Replacement
- Test your SSD/HDD using tools like CrystalDiskInfo
- Replace storage devices if errors persist

---

## 🔄 Summary

To fix `INACCESSIBLE_BOOT_DEVICE`, follow these steps:

1. Check storage mode (AHCI/RAID) in BIOS
2. Repair bootloader (BCD/MBR)
3. Remove bad updates or drivers
4. Run disk/file integrity checks
5. Restore or reset Windows
6. Test and replace hardware if needed

---

## 📎 Tags
`#Windows` `#BSOD` `#inaccessible-boot-device` `#boot-error` `#AHCI` `#RAID` `#fix` `#boot-drive` `#troubleshooting` `#UEFI` `#BCD` `#MBR`
