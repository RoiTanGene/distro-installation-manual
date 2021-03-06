## Setting up Booting
* **METHOD 1** (GRUB2)
    - Install `grub2`: `emerge -q sys-boot/grub:2`.
    - Install the necessary GRUB2 files to the `/boot/grub/` directory: `grub-install --target=x86_64-efi --efi-directory=/boot`.
    - Generate grub2 configuration: `grub-mkconfig -o /boot/grub/grub.cfg`.
    
* **METHOD 2** (EFISTUB) (**RECOMMENDED**)
- In order to boot directly from UEFI, the kernel needs to know where to find the root (/) partition of the system to be booted. Follow the guide showing what exact things needs to configued in the kernel: https://wiki.gentoo.org/wiki/EFI_stub_kernel for EFISTUB. Then:
    - Install `efibootmgr`: `emerge -q sys-boot/efibootmgr`.
    - Create the directory where the kernel image will be installed: `mkdir -p /boot/EFI/Gentoo`.
    - Copy the kernel image to appropriate place: `cp /usr/src/linux/arch/x86/boot/bzImage /boot/EFI/Gentoo/bzImage.efi`.
    - Create a EFI Boot entry for the kernel image to boot: `efibootmgr -c -d /dev/sdx -p 2 -L "Gentoo" -l '\EFI\Gentoo\bzImage.efi'`.