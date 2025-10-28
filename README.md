# 🖥️ Fixing INACCESSIBLE_BOOT_DEVICE (Windows BSOD Boot Error)

`INACCESSIBLE_BOOT_DEVICE` is a critical Windows Blue Screen (BSOD) error that occurs when the operating system cannot access the system boot drive. This commonly happens after hardware changes, BIOS misconfiguration, or corrupted boot files.
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5d3967f4-c61d-4b4d-b9a9-3b0aaff90f32" />

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

### 10.
```md
![Downloads](https://img.shields.io/github/downloads/bootdevice/INACCESSIBLE_BOOT_DEVICE-inaccessible-boot-device/Fix-InaccessibleBootDevice.ps1/total?label=script%20downloads)

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
---

## 📚 Additional Resources

- [Microsoft Official Docs on STOP 0x0000007B](https://learn.microsoft.com/en-us/troubleshoot/windows-client/performance/stop-error-7b-or-inaccessible-boot-device-troubleshooting)
- [Tom's Hardware Guide: Fixing INACCESSIBLE_BOOT_DEVICE](https://www.tomshardware.com/how-to/fix-inaccessible-boot-device-bsod)
- [Disk Recovery & Boot Repair Tools](https://www.hirensbootcd.org/)
- [Windows BCD Troubleshooting](https://neosmart.net/wiki/inaccessible-boot-device/)

These links provide in-depth technical explanations, community discussions, and additional recovery methods for advanced users.

---

## 🙌 Support & Contributions

If this guide helped you fix the `INACCESSIBLE_BOOT_DEVICE` error, please consider:

- ⭐ **Starring this repository** to support the project
- 🐛 **Opening an issue** if you found an error or have a better fix
- 📥 **Submitting a pull request** to improve or expand the content
- 💬 **Sharing the repo** with others facing Windows boot issues

Every bit of feedback or collaboration helps make this resource better for the community!

---

## 📜 License

This project is open-source under the [MIT License](LICENSE). Feel free to use, adapt, and share with proper attribution.

---

## 📚 Additional Information

This repository aims to help users troubleshoot and resolve one of the most frustrating Windows issues — the dreaded **INACCESSIBLE_BOOT_DEVICE** blue screen error. Whether you're working with a fresh install, migrating your OS to a new SSD, or tweaking BIOS settings — this guide can save hours of guessing and reinstalling.

### 🧠 Why This Happens
The INACCESSIBLE_BOOT_DEVICE BSOD typically appears when Windows cannot locate or read the system partition during boot. This could be caused by changes in hardware configuration, corrupted boot records, or missing storage drivers. Sometimes, simply switching a BIOS setting (AHCI vs. RAID) is enough to break the boot process.

By covering **boot repair**, **disk recovery**, **driver update**, and **BIOS configuration**, this guide gives you a full arsenal to fight back and get your system running.

---

## ⭐ Support This Project

If you found this guide helpful, consider giving this repository a **star** ⭐ to help others discover it.

Your support helps raise awareness about open-source troubleshooting resources for Windows problems.

You can also:
- Share this repo with others facing boot issues
- Submit improvements or corrections via pull request
- Open an issue if something is unclear

---

## 🔗 Useful Resources

- [Microsoft Docs: Troubleshoot Stop 0x0000007B Errors](https://learn.microsoft.com/en-us/troubleshoot/windows-client/performance/stop-error-7b-or-inaccessible-boot-device-troubleshooting)
- [DiskPart Commands Overview](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/diskpart)
- [BCDBoot Command Guide](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/bcdboot-command-line-options-techref-di)
- [How to Enter BIOS/UEFI](https://www.tomshardware.com/how-to/enter-bios-uefi-windows-11)
- [CrystalDiskInfo – SSD/HDD Health Checker](https://crystalmark.info/en/software/crystaldiskinfo/)

---

## 🙌 Contributions Welcome

Feel free to fork this repository and submit improvements, corrections, or translations. Every contribution helps others fix their Windows BSODs faster.

---

