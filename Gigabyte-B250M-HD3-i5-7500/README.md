```
rubel@rubel-B250M-HD3:~$ grep -i "model name" /proc/cpuinfo
model name	: Intel(R) Core(TM) i5-7500 CPU @ 3.40GHz
model name	: Intel(R) Core(TM) i5-7500 CPU @ 3.40GHz
model name	: Intel(R) Core(TM) i5-7500 CPU @ 3.40GHz
model name	: Intel(R) Core(TM) i5-7500 CPU @ 3.40GHz
rubel@rubel-B250M-HD3:~$ lspci | grep -i --color "vga\|3d\|2d"
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 630 (rev 04)
rubel@rubel-B250M-HD3:~$ dmidecode -t baseboard
dmidecode 3.2d
/sys/firmware/dmi/tables/smbios_entry_point: Permission denied
Scanning /dev/mem for entry point.
/dev/mem: Permission denied
rubel@rubel-B250M-HD3:~$ sudo dmidecode -t baseboard
[sudo] password for rubel: 

dmidecode 3.2
Getting SMBIOS data from sysfs.
SMBIOS 3.0.0 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: Gigabyte Technology Co., Ltd.
	Product Name: B250M-HD3-CF
	Version: x.x
	Serial Number: Default string
	Asset Tag: Default string
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: Default string
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

Handle 0x0021, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Enabled
	Description:    To Be Filled By O.E.M.

Handle 0x003A, DMI type 41, 11 bytes
Onboard Device
	Reference Designation:  Onboard IGD
	Type: Video
	Status: Enabled
	Type Instance: 1
	Bus Address: 0000:00:02.0

Handle 0x003B, DMI type 41, 11 bytes
Onboard Device
	Reference Designation:  Onboard LAN
	Type: Ethernet
	Status: Enabled
	Type Instance: 1
	Bus Address: 0000:00:19.0

Handle 0x003C, DMI type 41, 11 bytes
Onboard Device
	Reference Designation:  Onboard 1394
	Type: Other
	Status: Enabled
	Type Instance: 1
	Bus Address: 0000:03:1c.2

rubel@rubel-B250M-HD3:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
rubel@rubel-B250M-HD3:~$ lspci | grep -i network
rubel@rubel-B250M-HD3:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 0c
       serial: e0:d5:5e:00:f3:b8
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.13.0-30-generic firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 ioport:e000(size=256) memory:f7000000-f7000fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:3
       logical name: wlx00a0000038ef
       serial: 00:a0:00:00:38:ef
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=5.13.0-30-generic firmware=N/A ip=192.168.0.101 link=yes multicast=yes wireless=IEEE 802.11
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
rubel@rubel-B250M-HD3:~$ lshw -class disk -class storage
WARNING: you should run this program as super-user.
  *-sata                    
       description: SATA controller
       product: 200 Series PCH SATA controller [AHCI mode]
       vendor: Intel Corporation
       physical id: 17
       bus info: pci@0000:00:17.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: sata ahci_1.0 bus_master cap_list
       configuration: driver=ahci latency=0
       resources: irq:130 memory:f7228000-f7229fff memory:f722c000-f722c0ff ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:f722b000-f722b7ff
  *-storage
       description: Non-Volatile memory controller
       product: E12 NVMe Controller
       vendor: Phison Electronics Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: storage nvm_express bus_master cap_list
       configuration: driver=nvme latency=0
       resources: irq:16 memory:f7100000-f7103fff
     *-nvme0
          description: NVMe device
          product: PNY CS3030 500GB SSD
          physical id: 0
          logical name: /dev/nvme0
          version: CS303226
          serial: PNY1520023676010780E
          configuration: nqn=nqn.2014.08.org.nvmexpress:19871987PNY1520023676010780EPNY CS3030 500GB SSD state=live
        *-namespace
             description: NVMe namespace
             physical id: 1
             logical name: /dev/nvme0n1
  *-scsi
       physical id: d
       logical name: scsi0
       capabilities: emulated
     *-cdrom
          description: DVD writer
          product: iHAS124   F
          vendor: ATAPI
          physical id: 0.0.0
          bus info: scsi@0:0.0.0
          logical name: /dev/cdrom
          logical name: /dev/cdrw
          logical name: /dev/dvd
          logical name: /dev/dvdrw
          logical name: /dev/sr0
          version: CL9M
          capabilities: removable audio cd-r cd-rw dvd dvd-r
          configuration: ansiversion=5 status=nodisc
  *-scsi
       physical id: 1
       bus info: scsi@6
       logical name: scsi6
       capabilities: scsi-host
       configuration: driver=usb-storage
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
rubel@rubel-B250M-HD3:~$ 
```