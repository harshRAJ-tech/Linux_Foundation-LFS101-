
-------------------- LINUX Foundation ----------------------------

# ===== = INTRODUCTION = =====

Linux is a fully multi-tasking, multi-user operating system, with built-in networking and service processes known as daemons.

Linux is developed by a loose confederation of developers from all over the world, collaborating over the Internet, with Linus Torvalds at the head.

Technical skill and a desire to contribute are the only qualifications for participating.

Common terms used in Linux are: **kernel, distribution, boot loader, service, filesystem, X Window system, desktop environment, and command line.**

All Linux distribution consists of the **kernel** plus a number of other software tools for file-related operations, user management, and software package management.


---

# BASICS

## + The Boot Process
**Procedure for initializing the system** — it consists of from when the computer power is first switched on until the user interface is fully operational.


---

## BIOS (Basic Input/Output System)
- Initializes hardware including screen, keyboard, and tests the main memory.  
- Process also called **POST (Power On Self Test)**.  
- BIOS software stored in ROM chip of motherboard.  
- Remainder of boot process is controlled by the operating system.

---

## MBR / EFI Partition / Boot Loader
- POST completed through BIOS → **System control passes to Boot Loader**.  
- Boot loader stored in hard-disk / SSD disk (either in boot sector or EFI partition).  
- EFI (Extensible Firmware Interface or UEFI (Unified))  
- CMOS values keep track of date and time even when power is off.

Boot loaders include:
- **GRUB** (GRand Unified Bootloader)  
- **ISOLINUX** (booting from removable media)  
- **DAS U-Boot** (booting on embedded devices/appliances)

---

### BOOT LOADER IN ACTION
<img width="503" height="269" alt="image" src="https://github.com/user-attachments/assets/6faf9ce3-95ce-41a6-aebb-b0fb2d033bf0" />

**BIOS / MBR (Master Boot Record) size:** 512 bytes.

---

### Second-stage bootloader steps


---

# INITIAL RAM DISK

<img width="501" height="295" alt="image" src="https://github.com/user-attachments/assets/ad33063c-53a6-41f9-9f13-bb07a3e207b0" />

The **initramfs filesystem image** contains programs and binary files that perform all actions needed to mount the proper root file system, including:
- kernel functionality required for the specific filesystem,  
- loading device drivers for mass storage controllers (using **udev system**).

**udev system** is responsible for:
- figuring out which devices are present  
- loading device drivers  

---

## mount Program
The `mount` program instructs that the filesystem is ready for use and associates it with a particular point (its **mount point**).

When this is successful:
- **initramfs is cleared from RAM**,  
- The **init program** on the root filesystem (`/sbin/init`) is executed.

`init` handles:
- mounting  
- pivoting over to the final real root filesystem  

<img width="178" height="181" alt="image" src="https://github.com/user-attachments/assets/bf6439a8-8049-4448-b0c7-bc7f8b23e969" />

`init` starts a number of text-mode login prompts.

---

The default command shell is **bash (the GNU Bourne Again Shell)**.
