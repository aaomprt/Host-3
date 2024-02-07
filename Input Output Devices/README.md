# :game_die: Input/Output(I/O) devices :game_die:
อุปกรณ์ Input/Output: เป็นอุปกรณ์ที่ให้ข้อมูลเข้าสู่ระบบหรือรับข้อมูลจากระบบ เช่น คีย์บอร์ด, เมาส์, คีย์การ์ด, หน้าจอ, ปริ้นเตอร์, กล้องเว็บแคม, และอุปกรณ์เก็บข้อมูล

I/O ของแต่ละอุปกรณ์ เช่น keyboard, mouse, disk, printer, network adapter หรือ จอ monitor ทั้งหมดนี้ Kernel จะควบคุมการสื่อสารระหว่าง application และ hardware ให้

มีเครื่องมือหลายตัวที่ใช้สำหรับตรวจสอบข้อมูลฮาร์ดแวร์ของระบบ Linux ได้ บางคำสั่งจะรายงานข้อมูลทั้งหมดเช่น CPU, หน่วยประมวลผล, หน่วยความจำ, การจัดเก็บข้อมูล, ดิสก์ เป็นต้น และบางคำสั่งจะเน้นไปที่ส่วนของอุปกรณ์ฮาร์ดแวร์เฉพาะเช่น CPU, หน่วยประมวลผล, หน่วยความจำ เป็นต้น
เราจะพูดถึงเครื่องมือสำหรับข้อมูลอุปกรณ์ระบบ Linux เช่น lspci, lsscsi, lsusb, และ lsblk

<br><hr><br>

## :busstop: What’s lspci – List PCI Bus Devices: :bus:
  ![image](https://github.com/aaomprt/Host-3/assets/118121218/08b8ae27-b1a1-41d8-b963-78b0090746a2)
  มาจาก *Peripheral Component Interconnect* <br>
  
  lspci เป็นคำสั่งที่ใช้สำหรับแสดงข้อมูลเกี่ยวกับอุปกรณ์ที่เชื่อมต่อกับ PCI buses ในระบบและอุปกรณ์ฮาร์ดแวร์ที่เชื่อม
  ต่อกับ PCI และ PCI bus
  คำสั่ง lspci จะแสดงข้อมูลเกี่ยวกับหมายเลขรุ่น/รายละเอียดของชิปสำหรับอุปกรณ์เช่น PCI bridge, VGA
  controller, Ethernet controller, USB controller, Audio device, IDE interface ฯลฯ
  lspci เป็นส่วนหนึ่งของแพคเกจ pciutils
  
  สามารถใช้ได้โดยใช้รูปแบบ `lspci [option]`
  <br>
  
  ### :bulb: How to install lspci :bulb:
  สำหรับ Debian/Ubuntu, ใช้คำสั่ง apt-get หรือ apt เพื่อติดตั้ง pciutils
  ```
  $ sudo apt install pciutils
  ```

<br>

### lspci Usage  :page_with_curl:
  คำสั่ง lspci ใช้เพื่อแสดงข้อมูลเกี่ยวกับตัวควบคุม PCI ทั้งหมดบนระบบรวมถึงอุปกรณ์ที่เชื่อมต่ออยู่ด้วย


| อาร์กิวเมนต์ | คำอธิบาย | ตัวอย่าง |
| --- | :----------------------------------------------------: | --- |
| -v | แสดงผลลัพธ์แบบ verbose เพื่อแสดงข้อมูลเพิ่มเติมเกี่ยวกับแต่ละอุปกรณ์ | lspci -v |
| -nn | แสดงรหัสผู้ผลิตและรหัสอุปกรณ์ | lspci -nn |
| -k | แสดงไคเนลไดรเวอร์ที่จัดการกับแต่ละอุปกรณ์ | lspci -k |
| -t | แสดงอุปกรณ์ในรูปแบบTree | lspci -t |
| -i | ใช้ไฟล์ PCI ID ที่ระบุแทนการใช้ค่าเริ่มต้น | lspci -i /path/to/pci.ids |
| -d | แสดงเฉพาะอุปกรณ์ที่มีรหัสผู้ผลิตและรหัสอุปกรณ์ที่ระบุ | lspci -d 8086:100e |
| -s | แสดงเฉพาะอุปกรณ์ในบัสที่ระบุ | lspci -s 00:02.0 |
| -x | แสดงบรรทัดแรกของพื้นที่การกำหนดค่า | lspci -x |
| -xxx | แสดงพื้นที่การกำหนดค่าทั้งหมด (dangerous; root only). | lspci -xxx |
| -A | ใช้วิธีการเข้าถึงที่ระบุเพื่ออ่านพื้นที่การกำหนดค่าฮาร์ดแวร์ PCI | lspci -A intel-conf1 |
| -D | ให้แสดงหมายเลขโดเมนเสมอ | lspci -D |
| -F | อ่านการกำหนดค่าจากไฟล์ที่กำหนด | lspci -F dump.txt |

<br>

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


  ### ตัวอย่าง: สามารถใช้ตัวเลือก -t เพื่อแสดงเอาต์พุตในรูปแบบ Tree :deciduous_tree:
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


<br><hr><br>

## :cd: What’s lsscsi – List scsi Devices :cd:
  ![image](https://github.com/aaomprt/Host-3/assets/118121218/9805a937-efaf-455b-a9a0-2d13b398593f)
  lsscsi เป็นคำย่อของ *list small Computer System Interface* ซึ่งเป็นคำสั่งที่ใช้แสดงข้อมูลเกี่ยวกับอุปกรณ์ SCSI/Sata ที่เชื่อมต่อกับระบบ
  มันสแกน sysfs (ติดตั้งที่ /sys) เพื่อรวบรวมข้อมูล ซึ่งได้ถูกนำเข้ามาในซีรีส์เคอร์เนล Linux เวอร์ชัน 2.6
<br>
  ### :bulb: How to install lsscsi :bulb:
  สำหรับ Debian/Ubuntu, ใช้คำสั่ง apt-get หรือ apt เพื่อติดตั้ง lsscsi
  ```
  $ sudo apt install lsscsi
  ```
<br>

### lsscsi Usage :page_with_curl:
ใช้คำสั่งด้านล่างเพื่อดูข้อมูลอุปกรณ์ SCSI คำสั่งนี้จะแสดงรายละเอียดของอุปกรณ์ SCSI ที่เชื่อมต่อกับระบบ
หากต้องการดูอุปกรณ์ scsi/sata ทั้งหมด ให้ใช้คำสั่ง lsscsi ดังนี้
  ```
 ~ $ lsscsi

[0:0:0:0]    disk    ATA      ST1000LM024 HN-M 2BA3  /dev/sda 
[1:0:0:0]    cd/dvd  PLDS     DVD-RW DA8A5SH   RL61  /dev/sr0 
[4:0:0:0]    disk    Generic- xD/SD/M.S.       1.00  /dev/sdb 

  ```


ใช้ตัวเลือก -s เพื่อแสดงขนาดอุปกรณ์
  ```
 ~ $ lsscsi -s

[0:0:0:0]    disk    ATA      ST1000LM024 HN-M 2BA3  /dev/sda   1.00TB
[1:0:0:0]    cd/dvd  PLDS     DVD-RW DA8A5SH   RL61  /dev/sr0        -
[4:0:0:0]    disk    Generic- xD/SD/M.S.       1.00  /dev/sdb        -


  ```


<br><hr><br>

## :electric_plug: What’s lsusb – List USB buses and device :electric_plug:
![image](https://github.com/aaomprt/Host-3/assets/118121218/f320a47e-2f06-476e-8f21-6d079cb0a323)
lsusb ย่อมาจาก *list Universal Serial Bus* หรือ USB คำสั่งนี้จะแสดงข้อมูลเกี่ยวกับบัส USB ในระบบและอุปกรณ์ที่เชื่อมต่อกับบัสเหล่านั้น การใช้คำสั่งนี้จะแสดงรายการของอุปกรณ์ USB ทั้งหมดที่เชื่อมต่อกับคอมพิวเตอร์ เช่น แป้นพิมพ์ และเม้าส์ เครื่องพิมพ์ ไดรฟ์ดิสก์ เครือข่ายอะแดปเตอร์ ฯลฯ

<br>

### :bulb: How to install lsusb :bulb:
lsusb มีอยู่ในเรสโพรสิทอรี สำหรับ Debian/Ubuntu ใช้คำสั่ง apt-get หรือ apt เพื่อติดตั้ง lsusb

  ```
  $ sudo apt install usbutils
  ```

<br>

### lsusb Usage :page_with_curl:
สามารถใช้คำสั่ง lsusb ในการรายงานข้อมูลเกี่ยวกับตัวควบคุม USB และอุปกรณ์ทั้งหมดที่เชื่อมต่อ

  ```
  ~ $ lsusb
  
  Bus 001 Device 002: ID 8087:8000 Intel Corp. 
  Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
  Bus 002 Device 005: ID 0bda:b728 Realtek Semiconductor Corp. 
  Bus 002 Device 004: ID 5986:0249 Acer, Inc 
  Bus 002 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
  RTS5129 Card Reader Controller
  Bus 002 Device 002: ID 045e:00cb Microsoft Corp. 
  Basic Optical Mouse v2.0
  Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 
  2.0 root hub

  ```

สามารถใช้ตัวเลือก -v เพื่อแสดงข้อมูลโดยละเอียดเกี่ยวกับอุปกรณ์ USB แต่ละรายการ
  ```
   ~ $ lsusb -v
  ```

<br><hr><br>

## :computer: What’s lsblk – List block devices :pager:

![image](https://github.com/aaomprt/Host-3/assets/118121218/de579204-581e-4dd4-9b01-a909fcb4c8ff)

lsblk ย่อมาจาก *list of block devices* คำสั่งนี้จะแสดงข้อมูลเกี่ยวกับอุปกรณ์บล็อก (ยกเว้นดิสก์แรม) อุปกรณ์บล็อกรวมถึงพาร์ติชันฮาร์ดดิสก์ เมมโมรี่แฟลช ไดรฟ์ซีดี-รอม ไดรฟ์ออปติกอุปกรณ์ ฯลฯ
lsblk เป็นส่วนหนึ่งของแพ็กเกจ util-linux ซึ่งเป็นชุดเครื่องมือระดับพื้นฐานสำหรับระบบปฏิบัติการ Linux ซึ่งประกอบไปด้วยเครื่องมือระดับต่ำที่หลากหลายซึ่งจำเป็นสำหรับระบบ Linux ที่จะทำงานได้
<br>
### :bulb: How to install lsblk :bulb:
สำหรับ Debian/Ubuntu ใช้คำสั่ง apt-get หรือ apt เพื่อติดตั้ง lsblk
  ```
   $ sudo apt install util-linux
  ```
<br>

### lsblk Usage :page_with_curl:
block devices เป็นอุปกรณ์จัดเก็บข้อมูล เช่น ฮาร์ดดิสก์ แฟลชไดรฟ์ เป็นต้นใช้คำสั่ง lsblk เพื่อดูข้อมูลเกี่ยวกับ block devices ดังนี้

  ```
   ~ $ lsblk
  
  NAME    MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
  sda       8:0    0 931.5G  0 disk 
  ├─sda1    8:1    0  1000M  0 part 
  ├─sda2    8:2    0   260M  0 part /boot/efi
  ├─sda3    8:3    0  1000M  0 part 
  ├─sda4    8:4    0   128M  0 part 
  ├─sda5    8:5    0 557.1G  0 part 
  ├─sda6    8:6    0    25G  0 part 
  ├─sda7    8:7    0  14.7G  0 part 
  ├─sda8    8:8    0     1M  0 part 
  ├─sda9    8:9    0 324.5G  0 part /
  └─sda10   8:10   0   7.9G  0 part [SWAP]
  sr0      11:0    1  1024M  0 rom  

  ```

หากต้องการดู block devices ทั้งหมดในระบบให้ใส่ตัวเลือก -a


  ```
   ~ $ lsblk -a
  
  NAME    MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
  sda       8:0    0 931.5G  0 disk 
  ├─sda1    8:1    0  1000M  0 part 
  ├─sda2    8:2    0   260M  0 part /boot/efi
  ├─sda3    8:3    0  1000M  0 part 
  ├─sda4    8:4    0   128M  0 part 
  ├─sda5    8:5    0 557.1G  0 part 
  ├─sda6    8:6    0    25G  0 part 
  ├─sda7    8:7    0  14.7G  0 part 
  ├─sda8    8:8    0     1M  0 part 
  ├─sda9    8:9    0 324.5G  0 part /
  └─sda10   8:10   0   7.9G  0 part [SWAP]
  sdb       8:16   1         0 disk 
  sr0      11:0    1  1024M  0 rom  
  ram0      1:0    0    64M  0 disk 
  ram1      1:1    0    64M  0 disk 
  ram2      1:2    0    64M  0 disk 
  ram3      1:3    0    64M  0 disk 
  ram4      1:4    0    64M  0 disk 
  ram5      1:5    0    64M  0 disk 
  ram6      1:6    0    64M  0 disk 
  ram7      1:7    0    64M  0 disk 
  ram8      1:8    0    64M  0 disk 
  ram9      1:9    0    64M  0 disk 
  loop0     7:0    0         0 loop 
  loop1     7:1    0         0 loop 
  loop2     7:2    0         0 loop 
  loop3     7:3    0         0 loop 
  loop4     7:4    0         0 loop 
  loop5     7:5    0         0 loop 
  loop6     7:6    0         0 loop 
  loop7     7:7    0         0 loop 
  ram10     1:10   0    64M  0 disk 
  ram11     1:11   0    64M  0 disk 
  ram12     1:12   0    64M  0 disk 
  ram13     1:13   0    64M  0 disk 
  ram14     1:14   0    64M  0 disk 
  ram15     1:15   0    64M  0 disk 


  ```


<br><hr><br>

## :book: References :book:
- [2daygeek](https://www.2daygeek.com/check-system-hardware-devices-bus-information-lspci-lsscsi-lsusb-lsblk-linux/)<br />
- [th.linux](https://th.linux-console.net/?p=1357)<br />
- [borntodev](https://www.borntodev.com/wp-content/uploads/2023/08/cheatsheet-linux-command.pdf)<br />
- [hostpacific](https://www.hostpacific.com/command-linux/)<br />
- [Saixiii](https://saixiii.com/what-is-kernel/)<br />
- [ioflood](https://ioflood.com/blog/lspci-linux-command/)



