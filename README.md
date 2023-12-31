## 28.12.2023

### Аеророзвідка. User Stories.
- Очі богів. Як аеророзвідка наводить артилерію на атаки ворога: https://texty.org.ua/articles/111285/ochi-bohiv-den-na-zavdanni-iz-artylerijskoyu-aerorozvidkoyu/
- "Підіймаємо дрони, наводимо арту й відходимо". Як працює аеророзвідка ЗСУ на Донбасі: https://texty.org.ua/articles/106929/pidnimayemo-drony-navodymo-artu-i-vidkhodymo-jak-pratsjuye-aerorozvidka-na-donbasi/
- Фурія: https://uk.wikipedia.org/wiki/%D0%A4%D1%83%D1%80%D1%96%D1%8F_(%D0%91%D0%9F%D0%9B%D0%90)
- Фурія GS: https://uk.wikipedia.org/wiki/%D0%A4%D1%83%D1%80%D1%96%D1%8F_(%D0%91%D0%9F%D0%9B%D0%90)#/media/%D0%A4%D0%B0%D0%B9%D0%BB:UA_24th_brigade_Furia_02.jpg
- Фурія офіц. сайт: https://athlonavia.com/uk-furia/


### Trivia

- ger or set regulatory region: `$ iw reg get` `$ iw reg set GB`

## 27.12.2023

### Linux Wireless Regulatory
- Detailed overview: https://wireless.wiki.kernel.org/en/developers/regulatory
- *Central Regulatory Domain Agent (CRDA)*, a userspace agent, which can be triggered to update the kernel wireless core's definition of the regulatory permissions for a specific country.

### Backports!
- The *Backports Project* enables old kernels to run the latest drivers. https://backports.wiki.kernel.org/index.php/Main_Page
- "*Backporting* is the process of making new software run on something old. A version of something new that's been modified to run on something old is called a "backport".

### OpenWRT Build System Essentials (..being already sick of rereading it over and over, I'd rather write it down here)
- https://openwrt.org/docs/guide-developer/toolchain/buildsystem_essentials
- **meta** - mk files, config files, patches, etc.
- *target/linux* - contains different *targets* e.g. *target/linux/ar71xx" and the rest of it, e.g.: "target/linux/ar71xx/generic/profiles/some_models.ml", that is .mk files for target, subtargets and profiles. It also contains config files with config options!
- *target/* overall - meta for what has to be build (after tools?..): toolchain, linux - the firmware, sdk, imagebuilder - everything except packages
- *packages* - meta for packages to be build
- *staging_dir/packages/<target>/* <- built .ipk, including kernel modules are here, e.g. kmod-something.ipk
- *staging_dir/target.../root-...* contains “installed” versions of each target package again arranged with bin/, lib/, this will become the actual root directory that with some tweaking will get zipped up into the firmware image, something like root-ar71xx
- */lib/modules* on target system will contain compiled .o kernel modules 


### Trivia
- *musl libc*: small libc impl. for embedded: https://musl.libc.org/
- *24kc*: The 24Kc is a 32-bit RISC core for high performance applications
  Datasheet: https://s3-eu-west-1.amazonaws.com/downloads-mips/documents/MD00346-2B-24K-DTS-04.00.pdf
- http://linuxwireless.sipsolutions.net/en/developers/Documentation/Glossary/

### OpenWRT packaging structure:
- architecture > target > subtarget > profile
- *package architecture*: `"PKGARCH defaults to $(ARCH)_$(CPU_TYPE)"`. E.g.: "mips_24kc" - MIPS is the CPU type, 24kc is the exact CPU. OR: arm_cortex-a15_neon-vfpv4
- *target*: family of devices, sharing specific chipset:
"In OpenWrt slang, a target usually refers to a specific family of SoCs sharing the same or very similar CPU cores and instruction sets which are used among a range of different router models.
The ar71xx target for example refers to a series of MIPS CPU based SoCs first produced by Atheros (hence the AR prefix) and later Qualcomm."
- *subtarget*: narrowing device class down (like only devices with NAND or NOR flash memory within selected *target*)
- *profile*: e.g. exact model of device
- example card with all parameters for specific device: https://openwrt.org/toh/hwdata/abicominternational/abicominternational_scorpion_sc300m

### ar71xx vs ath79
- both are *targets* for specific atheros/qualcom chips
- ath79 is better arch due to using device tree instead of board files to describe specific device (explained here nicely: https://lwn.net/Articles/809248/)

"ar71xx vs. ath79 is not about drivers, but about the way the kernel is told about the hardware and how the kernel is compiled.
ar71xx uses board files (someboardname.c) specifying the exact hardware configuration of the machine. Depending on some other factors, you may have to compile a separate kernel for every machine of the same family, causing lots of build overhead. Generic kernels (like on x86) are not really feasible with board files. The upstream Linux kernel has deprecated board files for this and other reasons.
ath79 uses device tree (dts) to specify hardware configuration of the machine. Device tree is a textual machine description which is not compiled into the kernel, so you can simply build a single kernel compatible with hundreds of devices. You just have to supply the correct device tree files to the booting kernel, and the generic kernel will work fine. https://lwn.net/Articles/572692/ is a nice introduction to device tree, and it's fun to read."


### Linux Firmware:

- *firmware* in context of linux kernel: https://unix.stackexchange.com/questions/359989/what-is-firmware-in-linux-terminology

In the Linux kernel context, firmware is software which runs on another processor in the system, e.g. a wireless controller, a GPU, a SCSI controller... This software used to be stored in ROM (of various types) attached to the relevant controller, but to reduce costs and make upgrades simpler, controllers now tend to rely on the host operating system to load their firmware for them.

So firmware files aren’t used by the kernel, they’re loaded by the kernel onto other pieces of hardware. This is also what makes it vaguely acceptable to have software without source code in FLOSS systems: the argument goes that it’s not running on the main CPU but on another device.
  
- *linux-firmware*: Linux firmware is a package distributed alongside the Linux kernel that contains firmware binary blobs necessary for partial or full functionality of certain hardware devices.
https://wiki.gentoo.org/wiki/Linux_firmware
- why *blobs*: Firmware files are conventionally referred to as blobs because you cannot determine what they will do. Note that firmware is distributed under various different licenses which do not permit disassembly or reverse-engineering (see: detailed discussion of different kinds of firmware in Linux: https://www.linuxfromscratch.org/blfs/view/svn/postlfs/firmware.html)

### TOREAD:
- SecureBoot: https://bbs.archlinux.org/viewtopic.php?id=271423
- https://0pointer.net/blog/authenticated-boot-and-disk-encryption-on-linux.html

# WILT
What I've Learned Today
