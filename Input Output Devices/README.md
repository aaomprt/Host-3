# I/O Devices in Linux
อุปกรณ์ Input/Output: เป็นอุปกรณ์ที่ให้ข้อมูลเข้าสู่ระบบหรือรับข้อมูลจากระบบ เช่น คีย์บอร์ด, เมาส์, คีย์การ์ด, หน้าจอ, ปริ้นเตอร์, กล้องเว็บแคม, และอุปกรณ์เก็บข้อมูล เมื่อต้องการดูข้อมูลเกี่ยวกับอุปกรณ์ I/O, คำสั่งที่ใช้บ่อยมี lspci (แสดงข้อมูล PCI devices), lsusb (แสดงข้อมูล USB devices) และ lsblk (แสดงข้อมูล block devices)

### ตัวอย่างการใช้คำสั่ง lspci:
```
lspci
```

### ตัวอย่างการใช้คำสั่ง lsusb:
```
lsusb
```

ที่สำคัญและมีความสำคัญในระบบปฏิบัติการ Linux ในส่วนของ I/O Devices (อุปกรณ์ Input/Output) มีหลาย subcomponents ที่ทำหน้าที่ควบคุมและจัดการกับอุปกรณ์ที่ให้บริการ Input และ Output ต่าง ๆ ในระบบ เรามาดูรายละเอียดต่อไปนี้:


* Device Drivers (ไดรเวอร์อุปกรณ์): เป็นโปรแกรมที่ทำหน้าที่เป็นตัวกลางระหว่างระบบปฏิบัติการและอุปกรณ์ I/O ต่าง ๆ บนเครื่องคอมพิวเตอร์ ไดรเวอร์จะเป็นพาร์ทของ Kernel และทำหน้าที่แปลงคำสั่งที่ระบบส่งไปให้กับอุปกรณ์เป็นการควบคุมการทำงานของอุปกรณ์นั้น ๆ
  * คำสั่ง: lsmod (แสดงรายชื่อของ modules ที่กำลังทำงาน)
    ### ตัวอย่าง: lsmod
    ```
    lsmod
    ```
* Input Devices (อุปกรณ์ Input): รวมถึงอุปกรณ์ที่ให้ข้อมูลเข้าสู่ระบบ เช่น คีย์บอร์ด, เมาส์, คีย์การ์ด, และอุปกรณ์เซนเซอร์ต่าง ๆ เช่น กล้ามเนื้อ (joystick), และตัวเลขบนแป้นพิมพ์
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


|: — — :|


