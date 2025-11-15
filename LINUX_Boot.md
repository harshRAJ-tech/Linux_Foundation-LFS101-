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
+--------------------------------------------------------------+
|               SECOND STAGE BOOT LOADER (in /boot)            |
+--------------------------------------------------------------+
                 |
                 v
+--------------------------------------------------------------+
|   1. Displays splash screen / boot menu                      |
|      - User selects OS                                       |
|      - User selects kernel version                           |
+--------------------------------------------------------------+
                 |
                 v
+--------------------------------------------------------------+
|   2. Loads selected kernel into RAM                          |
|      - Bootloader finds vmlinuz (compressed kernel)          |
|      - Loads initramfs/initrd (initial filesystem)           |
+--------------------------------------------------------------+
                 |
                 v
+--------------------------------------------------------------+
|   3. Kernel begins execution                                 |
|      - Kernel is compressed                                  |
|      - First task: **Uncompress itself**                     |
+--------------------------------------------------------------+
                 |
                 v
+--------------------------------------------------------------+
|   4. Kernel detects system hardware                          |
|      - CPU, RAM, storage, buses                              |
|      - Identifies device controllers                         |
+--------------------------------------------------------------+
                 |
                 v
+--------------------------------------------------------------+
|   5. Kernel initializes device drivers                       |
|      - Built-in drivers                                      |
|      - Loads essential modules (if using initramfs)          |
+--------------------------------------------------------------+
                 |
                 v
+--------------------------------------------------------------+
|   SYSTEM IS NOW READY → moves to user-space (init/systemd)   |
+--------------------------------------------------------------+

        

      
