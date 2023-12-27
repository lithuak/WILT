
## 27.12.2023

### OpenWRT packaging structure:
- architecture > target > subtarget > profile
- *architecture*,
- *package architecture*: `"PKGARCH defaults to $(ARCH)_$(CPU_TYPE)"`. E.g.: "mips_24kc" - MIPS is the CPU type, 24kc is the exact CPU. OR: arm_cortex-a15_neon-vfpv4
- *target*: family of devices, sharing specific chipset:
"In OpenWrt slang, a target usually refers to a specific family of SoCs sharing the same or very similar CPU cores and instruction sets which are used among a range of different router models.
The ar71xx target for example refers to a series of MIPS CPU based SoCs first produced by Atheros (hence the AR prefix) and later Qualcomm."
- *subtarget*: narrowing device class down (like only devices with NAND or NOR flash memory within selected *target*)
- *profile*: e.g. exact model of device


### Linux Firmware:

- what is *firmware* in context of linux kernel: https://unix.stackexchange.com/questions/359989/what-is-firmware-in-linux-terminology

In the Linux kernel context, firmware is software which runs on another processor in the system, e.g. a wireless controller, a GPU, a SCSI controller... This software used to be stored in ROM (of various types) attached to the relevant controller, but to reduce costs and make upgrades simpler, controllers now tend to rely on the host operating system to load their firmware for them.

So firmware files aren’t used by the kernel, they’re loaded by the kernel onto other pieces of hardware. This is also what makes it vaguely acceptable to have software without source code in FLOSS systems: the argument goes that it’s not running on the main CPU but on another device.
  
- what is *linux-firmware*: Linux firmware is a package distributed alongside the Linux kernel that contains firmware binary blobs necessary for partial or full functionality of certain hardware devices.
https://wiki.gentoo.org/wiki/Linux_firmware
- wht *blobs*: Firmware files are conventionally referred to as blobs because you cannot determine what they will do. Note that firmware is distributed under various different licenses which do not permit disassembly or reverse-engineering (see: detailed discussion of different kinds of firmware in Linux: https://www.linuxfromscratch.org/blfs/view/svn/postlfs/firmware.html)

### TOREAD:
- SecureBoot: https://bbs.archlinux.org/viewtopic.php?id=271423
- https://0pointer.net/blog/authenticated-boot-and-disk-encryption-on-linux.html

# WILT
What I've Learned Today
