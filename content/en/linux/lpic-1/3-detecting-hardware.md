---
title: "3 Detecting hardware"
date: 2021-12-15T22:42:06+02:00
description: "How do I know my hardware is working properly?"
draft: false
enableToc: false
enableTocContent: false
tags:
-
series:
-
categories:

libraries:

---

## Determining hardware attached to the system

The one piece of hardware that is notorious for not installing correctly is the Graphics Card.
Usually this is easy enough to see. The system will default to a safe 800x600 resolution.
This is the resolution supported by most Graphics cards.
(We need to remember that Linux wasn't always a graphical OS. Servers do not need a Graphical user interface. This means that a Gui wasn't thought of until much later in the Linux lifetime)

When we use a computer, most of the time, we interact with the software. The kernel then interacts with the hardware on our behalf. This goes both ways.
This is called an abstraction layer.
The kernel uses a service called dbuss to identify hardware.
To see what hardware has been installed successfully, we can use a few shell commands.
(You will also see people call it Bash or terminal commands. The shell runs  the terminal and we interact with the shell. Bash is just  a version of shell. I want you to get into the habit of calling it shell as Bash is just a version of shell.)

### lspci

The first command that we are going to learn is lspci.
this is used to list PCI (peripheral connect interface) devices

```
lspci
```

Here is the results if I run lspci

```
░▒▓    ~  lspci                                         ✔  21:16:01  ▓▒░
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Root Complex
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 IOMMU
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge
00:01.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 PCIe GPP Bridge [6:0]
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Internal PCIe GPP Bridge 0 to Bus A
00:08.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Internal PCIe GPP Bridge 0 to Bus B
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 61)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 5
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 6
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 7
12:00.0 USB controller: Advanced Micro Devices, Inc. [AMD] Device 43bc (rev 02)
12:00.1 SATA controller: Advanced Micro Devices, Inc. [AMD] Device 43b8 (rev 02)
12:00.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43b3 (rev 02)
20:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
20:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
20:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
20:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
25:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
29:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Picasso (rev c9)
29:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Raven/Raven2/Fenghuang HDMI/DP Audio Controller
29:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) Platform Security Processor
29:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Raven USB 3.1
29:00.4 USB controller: Advanced Micro Devices, Inc. [AMD] Raven USB 3.1
29:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) HD Audio Controller
2a:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 61)

░▒▓    ~                                                ✔  21:16:05  ▓▒░
```

If you run lspci and your exact hardware does not show up, this does not mean that your hardware has been installed incorrectly. Alot of the time, a driver is written for multiple pieces of hardware. If you are unsure, it is best to just check and make sure.

### lsusb

lspci is good for detecting integrated hardware or hardware connected to PCI slots on your motherboard. But other harware might be removable and connected to USB interface.
For these, we use lsusb

```
lsusb
```
Below are the results if I run lsusb

```
░▒▓    ~  lsusb                                         ✔  21:24:03  ▓▒░
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 003: ID 09da:2690 A4Tech Co., Ltd. REDRAGON Live Camera
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 003 Device 003: ID 045e:0719 Microsoft Corp. Xbox 360 Wireless Adapter
Bus 003 Device 006: ID 045e:028f Microsoft Corp. Xbox360 Wireless Controller
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 258a:0012 HORI CO.,LTD DEGE 101 Optical Gaming Mouse
Bus 001 Device 002: ID 1b1c:0a3b Corsair Corsair HS60 Surround Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

░▒▓    ~                                                ✔  21:24:06  ▓▒░

```

Do not worry if hardware on a laptop is named differently. It could be that your built in touchpad is connected to a USB interface. It could be that it is manufactured by someone other than your laptop vendor. Just be sure to check if you are unsure.

## Hardware Names

When a system detects a piece of harware and successfully installs a driver, the harwre will get a name assigned to it. The system uses this name to interact with the hardware. To see al these names, we can run ls /dev/ (List devices)

```
ls /dev
```
Here is the output is I should run ls /dev

```
░▒▓    ~  ls /dev                                       ✔  21:24:06  ▓▒░
android          hugepages     sdb       tty25  tty53   ttyS23      vcs4
android2         hwrng         sdb1      tty26  tty54   ttyS24      vcs5
android3         input         sdc       tty27  tty55   ttyS25      vcs6
ashmem           kfd           sdc1      tty28  tty56   ttyS26      vcs7
autofs           kmsg          shm       tty29  tty57   ttyS27      vcsa
block            kvm           snapshot  tty3   tty58   ttyS28      vcsa1
bsg              lightnvm      snd       tty30  tty59   ttyS29      vcsa2
btrfs-control    log           stderr    tty31  tty6    ttyS3       vcsa3
bus              loop-control  stdin     tty32  tty60   ttyS30      vcsa4
char             mapper        stdout    tty33  tty61   ttyS31      vcsa5
console          media0        tpm0      tty34  tty62   ttyS4       vcsa6
core             mem           tpmrm0    tty35  tty63   ttyS5       vcsa7
cpu              mqueue        tty       tty36  tty7    ttyS6       vcsu
cpu_dma_latency  net           tty0      tty37  tty8    ttyS7       vcsu1
cuse             null          tty1      tty38  tty9    ttyS8       vcsu2
disk             nvram         tty10     tty39  ttyS0   ttyS9       vcsu3
dma_heap         port          tty11     tty4   ttyS1   udmabuf     vcsu4
dri              ppp           tty12     tty40  ttyS10  uhid        vcsu5
drm_dp_aux0      psaux         tty13     tty41  ttyS11  uinput      vcsu6
fb0              ptmx          tty14     tty42  ttyS12  urandom     vcsu7
fd               pts           tty15     tty43  ttyS13  usb         vfio
full             random        tty16     tty44  ttyS14  userio      vga_arbiter
fuse             rfkill        tty17     tty45  ttyS15  v4l         vhci
gpiochip0        rtc           tty18     tty46  ttyS16  vboxdrv     vhost-net
gpiochip1        rtc0          tty19     tty47  ttyS17  vboxdrvu    vhost-vsock
hidraw0          sda           tty2      tty48  ttyS18  vboxnetctl  video0
hidraw1          sda1          tty20     tty49  ttyS19  vboxusb     video1
hidraw2          sda2          tty21     tty5   ttyS2   vcs         video2
hidraw3          sda3          tty22     tty50  ttyS20  vcs1        watchdog
hidraw4          sda4          tty23     tty51  ttyS21  vcs2        watchdog0
hpet             sda5          tty24     tty52  ttyS22  vcs3        zero

░▒▓    ~                                                ✔  21:33:45  ▓▒░

```

Names are given to hardware by a service called udev.
Udev has a default set of names. Like if you were to connect a storage drive drive, this will show up as sd.
(standard disk) the first drive will be called sda and the partitions will be numbered (sda1 or sda2)
One could go into udev and rename devices if you so wish. Sometimes udev gives your hardware a long complex name and you want a simple short name to make it easier to work with.

The names are stored in /etc/udev

```
/etc/udev
```
Additional naming rules are stored inside the /etc/udev/rules.d

```
/etc/udev/rules.d
```
Do not panic if this folder is empty. It just means that the system is using default names determined by the kernel and the udev default set.

### lsmod

Drivers in Linux are loaded as kernel modules. These modules are loaded into RAM and the system can then interact with them.
It might be that your hardware is connected and detected inside or lspci or lsusb, but to see if the driver is present, we run lsmod (List Modules)

```
lsmod
```
Here is the output if I run lsmod

```
░▒▓    ~  lsmod                                         ✔  21:58:13  ▓▒░
Module                  Size  Used by
snd_seq_dummy          16384  0
snd_hrtimer            16384  1
snd_seq                86016  7 snd_seq_dummy
rfkill                 32768  1
intel_rapl_msr         20480  0
intel_rapl_common      28672  1 intel_rapl_msr
edac_mce_amd           36864  0
kvm_amd               147456  0
mousedev               24576  0
kvm                  1036288  1 kvm_amd
irqbypass              16384  1 kvm
amdgpu               7757824  160
crct10dif_pclmul       16384  1
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
btrfs                1638400  0
wmi_bmof               16384  0
joydev                 28672  0
snd_hda_codec_realtek   159744  1
uvcvideo              118784  0
aesni_intel           380928  0
gpu_sched              49152  1 amdgpu
videobuf2_vmalloc      20480  1 uvcvideo
snd_hda_codec_generic    98304  1 snd_hda_codec_realtek
i2c_algo_bit           16384  1 amdgpu
videobuf2_memops       20480  1 videobuf2_vmalloc
crypto_simd            16384  1 aesni_intel
drm_ttm_helper         16384  1 amdgpu
videobuf2_v4l2         36864  1 uvcvideo
ledtrig_audio          16384  1 snd_hda_codec_generic
blake2b_generic        20480  0
ttm                    86016  2 amdgpu,drm_ttm_helper
xor                    24576  1 btrfs
cryptd                 28672  2 crypto_simd,ghash_clmulni_intel
videobuf2_common       69632  4 videobuf2_vmalloc,videobuf2_v4l2,uvcvideo,videobuf2_memops
snd_hda_codec_hdmi     73728  1
rapl                   16384  0
raid6_pq              122880  1 btrfs
drm_kms_helper        299008  1 amdgpu
libcrc32c              16384  1 btrfs
snd_hda_intel          57344  2
sp5100_tco             20480  0
snd_usb_audio         352256  2
snd_intel_dspcfg       28672  1 snd_hda_intel
pcspkr                 16384  0
cec                    69632  1 drm_kms_helper
k10temp                16384  0
snd_intel_sdw_acpi     20480  1 snd_intel_dspcfg
i2c_piix4              28672  0
agpgart                45056  1 ttm
snd_usbmidi_lib        45056  1 snd_usb_audio
usbhid                 65536  0
snd_hda_codec         172032  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_rawmidi            45056  1 snd_usbmidi_lib
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
snd_seq_device         16384  2 snd_seq,snd_rawmidi
r8169                  98304  0
snd_hda_core          110592  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
sysimgblt              16384  1 drm_kms_helper
realtek                36864  1
fb_sys_fops            16384  1 drm_kms_helper
mdio_devres            16384  1 r8169
snd_hwdep              16384  2 snd_usb_audio,snd_hda_codec
ccp                   118784  1 kvm_amd
libphy                159744  3 r8169,mdio_devres,realtek
tpm_crb                20480  0
tpm_tis                16384  0
tpm_tis_core           28672  1 tpm_tis
tpm                    86016  3 tpm_tis,tpm_crb,tpm_tis_core
gpio_amdpt             20480  0
rng_core               16384  2 ccp,tpm
video                  57344  0
mac_hid                16384  0
pinctrl_amd            32768  0
gpio_generic           20480  1 gpio_amdpt
wmi                    36864  1 wmi_bmof
xpad                   45056  0
ff_memless             20480  1 xpad
vboxnetflt             32768  0
vboxnetadp             28672  0
vboxdrv               532480  2 vboxnetadp,vboxnetflt
snd_aloop              36864  1
snd_pcm               151552  6 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_aloop,snd_hda_core
snd_timer              45056  4 snd_seq,snd_hrtimer,snd_aloop,snd_pcm
snd                   114688  26 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_aloop,snd_pcm,snd_rawmidi
soundcore              16384  1 snd
v4l2loopback_dc        32768  0
videodev              270336  4 videobuf2_v4l2,v4l2loopback_dc,uvcvideo,videobuf2_common
mc                     65536  5 videodev,snd_usb_audio,videobuf2_v4l2,uvcvideo,videobuf2_common
drm                   585728  28 gpu_sched,drm_kms_helper,amdgpu,drm_ttm_helper,ttm
fuse                  167936  7
bpf_preload            16384  0
ip_tables              32768  0
x_tables               53248  1 ip_tables
ext4                  921600  2
crc32c_generic         16384  0
crc16                  16384  1 ext4
mbcache                16384  1 ext4
jbd2                  163840  1 ext4
xhci_pci               20480  0
crc32c_intel           24576  5
xhci_pci_renesas       20480  1 xhci_pci

░▒▓    ~                                                ✔  21:58:16  ▓▒░
```
If a module for a piece of hardware is not showing up, it will not work.

## Finding Drivers (Modules)

Linux is pretty robust. Most of the time everything just works the moment it is plugged in.
If this is not the case, You can go to the vendor website and download a package to install the missing module needed. In most cases, Packages will be available for Ubuntu, Redhat or Debian. If you remember the first part of this series, Installing Linux, you will remember that most of these packages can be interchangable around different distros of Linux.

## Disabling Hardware

There are some cases where you would want to disable hardware. An example of this usecase is when you have a USB ethernet adapter that just so happens to be faster than your onboard ethernet adapter and you want to disable the onboard one in favor of the USB one.

In this case, we would use rmmod (Remove Module)

```
rmmod
```
Now first we should go find the module we would want to remove. We could go through the entire list of lsmod to find it or we can have the system do it for us by piping the lsmod into another command. Piping a command just means that we take the output of one command to be the input of another command. This will be explained in greater detail later.
lsmod | grep bluetooth will look for the word bluetooth inside of the output of the lsmod command and display it

```
lsmod | grep bluetooth
```

Here is my output for lsmod | grep bluetooth

```
░▒▓    ~  lsmod | grep bluetooth                        ✔  22:16:28  ▓▒░

░▒▓    ~                                            0|1 ✘  22:16:30  ▓▒░

```
As you can clearly see, I have no bluetooth modules connected to my computer but if there were, I could run rmmod bluetooth to remove this module.

This module might be used by other modules in whc case, these modules should be removed using the same command.

This will only remove the kernel modules for the hardware. The hardware will still be detected but it will be disabled.

### Permanently disabling hardware

The rmmod method only diables modules until the next system reboot. To make the arrangement permanent, we make use of a blacklist. To disable hardware permanently we can load the module into /etc/modprobe.d.

## Reloading Modules

To reload modules, we use modprobe

```
modprobe
```

## Conclusion

Linux is great at detecting and installing hardware drivers
There are a few commands to see whether the hardware is connected and the drivers are installed.
You should be able to detect, install, enable, and disable software from now on.