-------------------- LINUX Foundation ----------------------------

 ===== = INTRODUCTION = =====
Linux is a fully multi-tasking, multi-user operating system, with built-in networking and service processes known as daemons.
Linux is developed by a loose confederation of developers from all over the world, collaborating over the Internet, with Linus Torvalds at the head.
Technical skill and a desire to contribute are the only qualifications for participating.
common terms used in Linux are: kernel, distribution, boot loader, service, filesystem, X Window system, desktop environment, and command line.
all Linux distribution consists of the kernel plus a number of other software tools for file-related operations, user management, and software package management.


BASICS

+ The Boot Process = procedure for initializing the system.  ----- it consists of from where the computer power is first switched on until the user unterface is fully operational.
+ Power ON ----> BIOS ----> Master boot record (MBR) or EFL Partition ---> Boot Loader (GRUB) ----> Kernel ---> Initial RAM disk ----> /sbin/iniy (parent process) ----> Command Sheel using getty ----> Graphical USer Interface

         BIOS (basic input/output system)
    - initialize hardware including screen keyboard and test the main memory. process also called (Power On Self Test)POST
    - BIOS software stored in ROM chip of motherboard. remainder of boot process is controled by operating system.

          MBR / EFI Partition / Boot Loader  
      - POST ---completed----through BIOS --- SYSTEM CONTROL PASSES----> Boot Loader.
      - boot loader [ stored in hard-disk / ssd disk either in boot sector or in EFI partition]
      EFI ( Extensible Firmware Interface  or UEFI(unified))    CMOS values (keep track of date and time even powered is off)
      - e GRUB (for GRand Unified Boot loader), ISOLINUX (for booting from removable media), and DAS U-Boot (for booting on embedded devices/appliances).
      -  BOOT LOADER IN ACTION ---------------
      - <img width="503" height="269" alt="image" src="https://github.com/user-attachments/assets/6faf9ce3-95ce-41a6-aebb-b0fb2d033bf0" />
      = BIOS / MBR(master boot record) size 512bytes.

Second-stage bootloader (/boot) → Shows splash screen/boot menu → User selects OS/kernel → Bootloader loads compressed kernel (vmlinuz) + initramfs into RAM → Kernel starts and uncompresses itself → Kernel detects hardware (CPU, RAM, storage, buses) → Kernel initializes built-in device drivers → Control passes to user-space (init/systemd)

  INITIAL RAM DISK  
<img width="501" height="295" alt="image" src="https://github.com/user-attachments/assets/ad33063c-53a6-41f9-9f13-bb07a3e207b0" />

  initramfs filesystem image contains preogram and binary files that perform all actions neeed to mount the proper root file system, including kernel functionality required or the specific filesystem that will be used, and loading the device drivers for mass storage controllers, by taking advantage of the udev system 

  udev system reponsible for figuiring out which device present / loading -- device drivers.

  *mount* program instructs filesystem is ready for use and associates it with a particular point (its mount points)
        
        *this is successful, the initramfs is cleared from RAM, and the init program on the root filesystem (/sbin/init) is executed.*
 init handles the mounting and pivoting over to the final real root filesystem.
 <img width="178" height="181" alt="image" src="https://github.com/user-attachments/assets/bf6439a8-8049-4448-b0c7-bc7f8b23e969" /> init starts a number of text-mode login prompts.

the default command shell is bash (the GNU Bourne Again Shell),
        
      
