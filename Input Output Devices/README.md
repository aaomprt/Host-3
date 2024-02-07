# Input/Output(I/O) devices
อุปกรณ์ Input/Output: เป็นอุปกรณ์ที่ให้ข้อมูลเข้าสู่ระบบหรือรับข้อมูลจากระบบ เช่น คีย์บอร์ด, เมาส์, คีย์การ์ด, หน้าจอ, ปริ้นเตอร์, กล้องเว็บแคม, และอุปกรณ์เก็บข้อมูล

I/O ของแต่ละอุปกรณ์ เช่น keyboard, mouse, disk, printer, network adapter หรือ จอ monitor ทั้งหมดนี้ Kernel จะควบคุมการสื่อสารระหว่าง application และ hardware ให้

มีเครื่องมือหลายตัวที่ใช้สำหรับตรวจสอบข้อมูลฮาร์ดแวร์ของระบบ Linux ได้ บางคำสั่งจะรายงานข้อมูลทั้งหมดเช่น CPU, หน่วยประมวลผล, หน่วยความจำ, การจัดเก็บข้อมูล, ดิสก์ เป็นต้น และบางคำสั่งจะเน้นไปที่ส่วนของอุปกรณ์ฮาร์ดแวร์เฉพาะเช่น CPU, หน่วยประมวลผล, หน่วยความจำ เป็นต้น
เราจะพูดถึงเครื่องมือสำหรับข้อมูลอุปกรณ์ระบบ Linux เช่น lspci, lsscsi, lsusb, และ lsblk



### What’s lspci – List PCI Bus Devices:
  ![image](https://github.com/aaomprt/Host-3/assets/118121218/08b8ae27-b1a1-41d8-b963-78b0090746a2)
  มาจาก Peripheral Component Interconnect
  lspci เป็นคำสั่งที่ใช้สำหรับแสดงข้อมูลเกี่ยวกับอุปกรณ์ที่เชื่อมต่อกับ PCI buses ในระบบและอุปกรณ์ฮาร์ดแวร์ที่เชื่อ
  ต่อกับ PCI และ PCI bus
  คำสั่ง lspci จะแสดงข้อมูลเกี่ยวกับหมายเลขรุ่น/รายละเอียดของชิปสำหรับอุปกรณ์เช่น PCI bridge, VGA
  controller, Ethernet controller, USB controller, Audio device, IDE interface ฯลฯ
  lspci เป็นส่วนหนึ่งของแพคเกจ pciutils
  
  สามารถใช้ได้โดยใช้รูปแบบ lspci [option]

### How to install lspci
  สำหรับ Debian/Ubuntu, ใช้คำสั่ง apt-get หรือ apt เพื่อติดตั้ง pciutils
  ```
  $ sudo apt install pciutils
  ```
### lspci Usage
  คำสั่ง lspci ใช้เพื่อแสดงข้อมูลเกี่ยวกับตัวควบคุม PCI ทั้งหมดบนระบบรวมถึงอุปกรณ์ที่เชื่อมต่ออยู่ด้วย
  อาร์กิวเมนต์ คำอธิบาย ตัวอย่าง


    | อาร์กิวเมนต์ | คำอธิบาย | ตัวอย่าง |
    | :---: | --- | --- |
    | -v | แสดงผลลัพธ์แบบ verbose เพื่อแสดงข้อมูลเพิ่มเติมเกี่ยวกับแต่ละอุปกรณ์ | lspci -v
    | -nn | แสดงรหัสผู้ผลิตและรหัสอุปกรณ์ | lspci -nn
    | -k | แสดงไคเนลไดรเวอร์ที่จัดการกับแต่ละอุปกรณ์ | lspci -k
    | -t | แสดงอุปกรณ์ในรูปแบบเหมือนต้นไม้ | lspci -t
    | -i | ใช้ไฟล์ PCI ID ที่ระบุแทนการใช้ค่าเริ่มต้น | lspci -i /path/to/pci.ids
    | -d | แสดงเฉพาะอุปกรณ์ที่มีรหัสผู้ผลิตและรหัสอุปกรณ์ที่ระบุ | lspci -d 8086:100e
    | -s | แสดงเฉพาะอุปกรณ์ในบัสที่ระบุ | lspci -s 00:02.0
    | -x | แสดงบรรทัดแรกของพื้นที่การกำหนดค่า | lspci -x
    | -xxx | แสดงพื้นที่การกำหนดค่าทั้งหมด (เสี่ยงต่อความเสี่ยง; สำหรับ root เท่านั้น) | lspci -xxx
    | -A | ใช้วิธีการเข้าถึงที่ระบุเพื่ออ่านพื้นที่การกำหนดค่าฮาร์ดแวร์ PCI | lspci -A intel-conf1
    | -D | แสดงหมายเลขโดเมนเสมอ | lspci -D
    | -F | อ่านการกำหนดค่าจากไฟล์ที่กำหนด | lspci -F dump.txt

  ### ตัวอย่าง: ต้องการดูข้อมูลเกี่ยวกับอุปกรณ์ PCI ให้รันคำสั่งต่อไปนี้
  ```
  ~ $ lspci
  00:00.0 Host bridge: Intel Corporation Haswell-ULT 
  DRAM Controller (rev 0b)
  00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT 
  Integrated Graphics Controller (rev 0b)
  00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller
  (rev 0b)
  00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC 
  (rev 04)
  00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 
  (rev 04)
  00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller 
  (rev 04)
  00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 
  (rev e4)
  00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 
  (rev e4)
  00:1c.4 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 5 
  (rev e4)
  00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 
  (rev 04)
  00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller 
  (rev 04)
  00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 
  [AHCI mode] (rev 04)
  00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
  01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 
  PCI Express Gigabit Ethernet Controller (rev 10)
  02:00.0 Network controller: Realtek Semiconductor Co., Ltd. 
  RTL8723BE PCIe Wireless Network Adapter
  03:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 840M] (rev a2)

  ```


  ### ตัวอย่าง: สามารถใช้ตัวเลือก -t เพื่อแสดงเอาต์พุตในรูปแบบ Tree
  ```
   ~ $ lspci -t
  -[0000:00]-+-00.0
           +-02.0
           +-03.0
           +-14.0
           +-16.0
           +-1b.0
           +-1c.0-[01]----00.0
           +-1c.3-[02]----00.0
           +-1c.4-[03]----00.0
           +-1d.0
           +-1f.0
           +-1f.2
           \-1f.3

  ```



  ### ตัวอย่าง: สามารถใช้ตัวเลือก -v เพื่อแสดงข้อมูลโดยละเอียดเกี่ยวกับอุปกรณ์ที่เชื่อมต่อแต่ละเครื่อง
  ```
  ~ $ lspci -v
  00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
  	Subsystem: Lenovo Device 3978
  	Flags: bus master, fast devsel, latency 0
  	Capabilities: 
  
  00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT 
  Integrated Graphics Controller (rev 0b) (prog-if 00 [VGA controller])
  	Subsystem: Lenovo Device 380d
  	Flags: bus master, fast devsel, latency 0, IRQ 62
  	Memory at c3000000 (64-bit, non-prefetchable) [size=4M]
  	Memory at d0000000 (64-bit, prefetchable) [size=256M]
  	I/O ports at 6000 [size=64]
  	Expansion ROM at  [disabled]
  	Capabilities: 
  	Kernel driver in use: i915
  .....

  ```




### What’s lsscsi – List scsi Devices
  ![image](https://github.com/aaomprt/Host-3/assets/118121218/9805a937-efaf-455b-a9a0-2d13b398593f)





### Input Devices (อุปกรณ์ Input): รวมถึงอุปกรณ์ที่ให้ข้อมูลเข้าสู่ระบบ เช่น คีย์บอร์ด, เมาส์, คีย์การ์ด, และอุปกรณ์เซนเซอร์ต่าง ๆ เช่น กล้ามเนื้อ (joystick), และตัวเลขบนแป้นพิมพ์
    * คำสั่ง: lsinput (แสดงรายชื่อและคุณสมบัติของอุปกรณ์ Input)
      ### ตัวอย่าง: lsinput
      ```
      lsinput
      ```
* Output Devices (อุปกรณ์ Output): รวมถึงอุปกรณ์ที่ให้ข้อมูลออกจากระบบ เช่น หน้าจอ (monitor), ปริ้นเตอร์, ลำโพง, และอุปกรณ์ที่ให้ผลลัพธ์ทางกล้ามเนื้อ เช่น มอเตอร์
    * คำสั่ง: xrandr (แสดงและกำหนดค่าหน้าจอและการแสดงผล)
      ### ตัวอย่าง: xrandr
      ```
      xrandr
      ```
* Bus Systems (ระบบบัส): ระบบทางกลางที่ใช้ในการเชื่อมต่อ I/O Controllers กับ CPU และ Memory ในรูปแบบของสัญญาณสายที่ถูกออกแบบมาเพื่อรองรับความเร็วและประสิทธิภาพที่ต้องการ ส่วนหนึ่งของระบบบัสที่ใช้ทั่วไปคือ PCI Express (PCIe)
   * คำสั่ง: lscpu (แสดงข้อมูลเกี่ยวกับ CPU และระบบบัส)
     ### ตัวอย่าง: lscpu
     ```
     lscpu
     ```

     
* I/O Controllers (ควบคุมอุปกรณ์ Input/Output): เป็นส่วนที่ควบคุมการสื่อสารระหว่าง CPU และอุปกรณ์ I/O โดยทำหน้าที่ควบคุมการส่งข้อมูล, การรับข้อมูล, และการจัดการสัญญาณ I/O
   * คำสั่ง: lspci (แสดงข้อมูล PCI devices)
     ### ตัวอย่าง: lspci
     ```
     lspci
     ```
     
* List PCI Bus Devices/DMA Controllers (ควบคุมการถ่ายโอนข้อมูลโดยไม่ใช้ CPU): Direct Memory Access (DMA) Controllers ทำให้อุปกรณ์ I/O สามารถถ่ายโอนข้อมูลไปยังหรือจากระบบหน่วยความจำโดยตรงโดยไม่ต้องผ่าน CPU ทำให้ประสิทธิภาพการถ่ายโอนข้อมูลมีประสิทธิภาพมากขึ้น
lspci stands for list PCI devices. lspci command is used to display information about PCI buses in the system and hardware devices that are connected to PCI and PCI bus. It will display information about model number/chip details for devices like PCI bridge, VGA controller, Ethernet controller, USB controller, Audio device, IDE interface, etc,., lspci doesn’t come stand alone utility and its part of the pciutils package. By default, it shows a brief list of devices which are attached in the system, so filter out specific device information with grep for better view.
   * คำสั่ง: lspci -v (แสดงข้อมูล PCI devices พร้อมรายละเอียด) To display the detailed information of all the PCI devices
     ### ตัวอย่าง: lspci -v
     ```
     lspci -v
     ```
   * คำสั่ง: lspci -m To display the subsystem information.
     ```
     lspci -m
     ```


     
* List block devices lsblk stands for list block devices. It’s display information about block devices (except RAM disks). Block devices are hard disk partition, flash drives, CD-ROM, optical drives, etc,. lsblk is part of the util-linux package. It’s collection of basic system utilities that contains a large variety of low-level system utilities that are necessary for a Linux system to function.
  * lsblk Usage 
     Just run the following command to get the block device information.
     ### ตัวอย่าง: lsblk
     ```
    lsblk
    NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
    loop0    7:0    0 81.4M  1 loop /snap/core/2898
    loop1    7:1    0  8.4M  1 loop /snap/gping/13
    sda      8:0    0   30G  0 disk 
    └─sda1   8:1    0   30G  0 part /
    sr0     11:0    1 1024M  0 rom  
     ```

      ### Details:
       * NAME: Device Name listed here
       * MAJ:MIN: Shows major and minor device number
       * RM: Shows whether the device is removable or not
       * SIZE: Dispaly size of the device
       * RO: Display if the device is read-only
       * TYPE: Display about device type such as disk, partition, lvm, etc.,
       * MOUNTPOINT: Dispaly where the device is mounted

     ### ตัวอย่าง: lsblk
     ```
    lsblk -m
     ```





* List USB buses and device lsusb stands for list Universal Serial Bus or USB. It’s display information about USB buses in the system and the devices connected to them. This will display a list of all USB devices connected to your computer such as keyboards, mouse, printers, disk drives, network adapters, etc.,. lsusb doesn’t come stand alone utility and its part of the usbutils package.
  * lsusb Usage
     Just run the following command to get the USB device information.
     ### ตัวอย่าง: lsusb
     ```
    lsusb
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
    Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
    Bus 002 Device 003: ID ffff:0248
    Bus 002 Device 005: ID 04b3:4010 IBM Corp.
     ```

      ### Details:
       * Bus 002: Which bus the device is attached
       * Device 005: It’s attached as fifth device
       * ID 04b3:4010: It’s device identification number
       * IBM Corp: Manufacture Name
 





* List scsi Devices lsscsi stands for list small Computer System Interface. The lsscsi command lists information about SCSI/Sata devices attached to the system. It scans the sysfs (mounted at /sys) pseudo file system to gather information, which was introduced in the 2.6 Linux kernel series.
  * lspci Usage
     Just run the following command to get the SCSI device information.
     ### ตัวอย่าง: lsusb
     ```
    lsscsi
    [0:2:0:0]    disk    IBM      ServeRAID M5110e 3.24  /dev/sda
    [0:2:1:0]    disk    IBM      ServeRAID M5110e 3.24  /dev/sdb
    [2:0:0:0]    cd/dvd  IBM SATA  DEVICE 62F2642  SA82  /dev/sr0
     ```


References |
---------- |
[2daygeek](https://www.2daygeek.com/check-system-hardware-devices-bus-information-lspci-lsscsi-lsusb-lsblk-linux/)
[th.linux-console](https://th.linux-console.net/?p=1357)
[borntodev](https://www.borntodev.com/wp-content/uploads/2023/08/cheatsheet-linux-command.pdf)
[hostpacific](https://www.hostpacific.com/command-linux/)
