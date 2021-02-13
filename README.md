# Utility for compiling out of tree kernel moduels for pCP Kernels


Recommended repos for Realtek drivers.... but there are many.  There build options for these packages can be
quite different.

Notes: In all cases, you will need to edit Makefile
* Set all the CONFIG_PLATFORM* = n
* Then set CONFIG_PLATFORM_ARM_RPI = y   (or CONFIG_PLATFORM_ARM64_RPI = y) whichever closest matches your system.
* Driver specific notes are shown below.

8188eu - https://github.com/aircrack-ng/rtl8188eus [branch "v5.3.9"]

8188fu - https://github.com/kelebek333/rtl8188fu [branch "master"]

8192eu - https://github.com/Mange/rtl8192eu-linux-driver [branch "realtek-4.4.x"]

8812au - https://github.com/aircrack-ng/rtl8812au [branch "v5.6.4.2"]

8822bu - https://github.com/EntropicEffect/rtl8822bu [branch "master"]

8821cu - https://github.com/brektrou/rtl8821CU [branch "master"]
* Makefile uses KVER instead of the normal KERNELVERSION variable
* export KVER=$KERNELRELEASE
* unset KERNELRELEASE
* This driver utilizes floating point, which is not normal for kernel drivers. The readme at the git repo describes how to edit the kernel source to allow building for rpi.

