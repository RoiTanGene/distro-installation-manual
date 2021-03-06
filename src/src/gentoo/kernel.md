## Installing The Linux Kernel
* **METHOD 1** (linux-pf)
  - Merge the pf kernel: `emerge -q sys-kernel/pf-sources`.
  - Select the kernel: `eselect kernel set 1`.
  - Change the directory: `cd /usr/src/linux`.
  - Configure the kernel using menu-driven configuration screen: `make --jobs "$(nproc || printf '%s\n' 1)" menuconfig`.
  - **OR** Configure the kernel (Update current config disabling modules not loaded): `make --jobs "$(nproc || printf '%s\n' 1)" localmodconfig`.
  - Compile the kernel: `make --jobs "$(nproc || printf '%s\n' 1)"`.
  - Install the kernel modules: `make --jobs "$(nproc || printf '%s\n' 1)" modules_install`.
  - Copy the kernel image to `/boot/`: `make --jobs "$(nproc || printf '%s\n' 1)" install`.

* **METHOD 2** (linux) (**RECOMMENDED**)
  - Create the directory if not exist: `mkdir -p /usr/src/`.
  - Change to the directory: `cd /usr/src/`.
  - Download the latest stable kernel from [kernel.org](https://www.kernel.org/): `wget https://cdn.kernel.org/pub/linux/kernel/vx.x/linux-x.x.x.tar.xz`.
  - Extract the kernel: `tar -xvf linux-x.x.x.tar.xz`.
  - Change the kernel directory name: `mv linux-x.x.x.tar.xz linux`.
  - Change to the kernel directory: `cd linux`.
  - Configure the kernel using menu-driven configuration screen: `make --jobs "$(nproc || printf '%s\n' 1)" menuconfig`.
  - **OR** Configure the kernel (Update current config disabling modules not loaded): `make --jobs "$(nproc || printf '%s\n' 1)" localmodconfig`.
  - Compile the kernel: `make --jobs "$(nproc || printf '%s\n' 1)" make`.
  - Install the kernel modules: `make --jobs "$(nproc || printf '%s\n' 1)" modules_install`.
  - Copy the kernel image to `/boot/`: `make --jobs "$(nproc || printf '%s\n' 1)" install`.