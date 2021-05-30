# Utility for compiling out of tree kernel moduels for pCP Kernels

## Start
* Step 1: Download the two scripts:
 * cd ~/.local/bin
 * wget https://github.com/piCorePlayer/pCP-Kernels/raw/master/pcp_prepare_kernel_src
 * wget https://github.com/piCorePlayer/pCP-Kernels/raw/master/pcp_make_module_extension
 * chmod 755 pcp*
* Step 2: Prepare the kernel source...this will download the source if needed.  Note: kernel source is over 160MB, you will likely need about 300MB of free space to perform these tasks.
 * run: pcp_prepare_kernel_src -s <path to saved pCP kernel source - or where to save it>
* Step 3: Compile your driver based on notes below, driver source code, and information from step 2.
* Step 4: Build the extension that contains the driver.
  * Run: pcp_make_module_extension -e < extension name >
  * Make sure to run this command from the source directory of your driver.
 

### Recommended repos for Realtek drivers....but there are many.  There build options for these packages can be quite different.

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
* This driver utilizes floating point, which is not normal for kernel drivers. The readme at the git repo describes how to edit the kernel source to allow building for rpi.

