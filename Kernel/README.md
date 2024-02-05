--- kernel ---


------ครึ่งหลัง------------------

## Kernel Module
### Configuration
  - คำสั่ง **modprobe** สามารถใช้เพิ่มหรือลบโมดูลได้ โดยมีไฟล์ .conf ทั้งหมดภายในส่วนขยายไดเร็กทอรี /etc/modprobe.d สำหรับระบุตัวเลือกที่จำเป็นสำหรับโมดูลต่างๆ 
  - file configuration สามารถใช้สร้าง alias (นามแฝงสำหรับโมดูล) หรือเปลี่ยนแปลงลักษณะการทำงานของ modprobe ตามความต้องการ
  - ไฟล์ .conf อยู่ในไดเร็กทอรี /etc/modprobe.d และใน Linux เวอร์ชันเก่า จะอยู่ในไฟล์ /etc/modprobe.conf

**Loadable module**
 - สามารถกำหนดค่าในไฟล์ .conf ที่อยู่ในไดเรกทอรี /etc/modules-load.d เพื่อโหลดโมดูลเหล่านั้นขณะที่ระบบกำลังเริ่มในส่วนของ init ของกระบวนการบูต
 - ทุกโมดูลจะถูกระบุหนึ่งโมดูลต่อ 1 บรรทัด เช่นสร้างไฟล์ /etc/modules.d/networking.conf และกำหนดโมดูลให้มีการโหลด 3 รายการดังนี้
   ```
   tun
   e1000e
   brcmfmac
   ```
- การจำกัดไม่ให้โมดูลถูกโหลด ให้ทำการเพิ่มชื่อของโมดูลลงในไฟล์ที่อยู่ใน /etc/modprobe.d/ และให้เริ่มต้นทุกชื่อโมดูลด้วย "blacklist"
  ```
  blacklist uhci_hcd
  blacklist nvidia
  ```
- การสร้างชื่อแฝง (alias) สำหรับชื่อโมดูล สามารถสร้างfile .conf /etc/modprobe.d/ เช่น myalias.conf และ กำหนดผ่านโครงสร้าง alias [alias] [module name]
  ตัวอย่างด้านล่างเป็นการสร้าง alias mymod แทนชื่อโมดูลที่ยาวเกินไป
  ```
    alias mymod really_long_module_name
  ```
### Kernel Paramiters
- ไดเรกทอรี /proc/sys มีไฟล์และไดเรกทอรีหลายรายการที่มีประโยชน์ในการเปลี่ยนแปลงการตั้งค่าของคอนเน็กเตอร์ มีประโยชน์เมื่อต้องการแก้ปัญหาหรือปรับแต่งระบบ Linux

  ไดเรกทอรี /proc/sys ถูกแบ่งออกเป็นไดเรกทอรีย่อยได้แก่:

  | Subdirectory | What it is |
  | :---: | --- |
  | abi/ | Execution domains & personalities |
  | debug/ | <empty> |
  | dev/ |Device specific information (eg dev/cdrom/info)|
  | fs/ | Specific filesystems filehandle, inode, dentry and quota tuning binfmt_misc <Documentation/admin-guide/binfmt-misc.rst> |
  | kernel/ | Global kernel info / tuning miscellaneous stuff |
  | net/ | Networking stuff, for documentation look in: <Documentation/networking/> |
  | vm/ | Memory management tuning buffer and cache management |
  | user/ | Per user per user namespace limits |

**The sysctl Command**

- คำสั่ง sysctl เป็นเครื่องมือซอฟต์แวร์ที่อ่านและปรับเปลี่ยนคุณสมบัติของ kernel เช่น เวอร์ชัน, maximum limits, และการตั้งค่าความปลอดภัย
- สามารถใช้งานได้ทั้งในโหมดแบบอินเทอร์แอคทีฟและแบบสคริปต์
- Syntax:
  ```
  sysctl [ OPTIONS ]
  ```
  | Options | Options Meaning |
  | :---: | --- |
  | -a, --all | Display all values currently available. |
  | -e, --ignore | Use this option to ignore errors about unknown keys. |
  | -p [FILENAME}, --load[=FILENAME] | Load in sysctl settings from the file specified or /etc/sysctl.conf if none given. |
  | -r, --pattern pattern | Only apply settings that match pattern. |
  | -w, --write | Use this option when you want to change a sysctl setting. |

- การดูว่า attributes มีอะไรบ้างให้ใช้คำสั่ง -a จะทำการแสดงผล parameters ทั้งหมดที่มีการ config ในปัจจุบัน
  ```
  host-3@host-3-server$ sysctl -a
  abi.vsyscall32 = 1
  debug.exception-trace = 1
  debug.kprobes-optimization = 1
  dev.cdrom.autoclose = 1
  dev.cdrom.autoeject = 0
  dev.cdrom.check_media = 0
  dev.cdrom.debug = 0
  dev.cdrom.info = CD-ROM information, Id: cdrom.c 3.20 2003/12/17
  ```

**The sysctl.conf File**
- systcl preload และ configuration file สามารถกำหนดได้ที่ /etc/sysctl.d/99-sysctl.conf
- การกำหนดค่าแต่ละอย่างจะอยู่ภายในไฟล์ต่างๆ ภายใน etc/sysctl.d 
- การเปลี่ยนแปลงตั้งค่าสามารถทำได้ผ่านการจัดการไฟล์หรือใช้ sysctl
- ตัวอย่างคำสั่งต่อไปนี้จะเป็นการเปลี่ยนแปลงค่าของพารามิเตอร์ kernel.sysrq จนกว่าระบบจะถูกรีบูต
  ```
  host-3@host-3-server$ sysctl kernel.sysrq=1
  ```
- หากต้องการรักษาการเปลี่ยนแปลงระหว่างรีบูต ให้ทำเพิ่มหรือแก้ไขบรรทัดที่ต้องการในไฟล์ /etc/sysctl.d/99-sysctl.conf หรือสร้างไฟล์พารามิเตอร์ที่เกี่ยวข้องในไดเรกทอรี /etc/sysctl.d/

### Monitoring
**The /proc Directory**
- ไฟล์ /proc เป็น virtual filesystem ตัวหนึ่ง บางครั้งถูกเรียกว่า pseudo-file system ของข้อมูลของ process
- ถือเป็นศูนย์ควบคุมและข้อมูลสำหรับ kernel เนื่องจากส่วนใหญ่ของเครื่องมือระบบก็เป็นการเรียกใช้ไฟล์ในไดเรกทอรีนี้ ตัวอย่างเช่น 'lsmod' เป็นเหมือนกับ 'cat /proc/modules' เป็นต้น
- การแก้ไขไฟล์ในไดเรกทอรี จะสามารถอ่าน/แก้ไขพารามิเตอร์ของ kernel(sysctl) ได้ในขณะที่ระบบกำลังทำงาน
  
  | Directories | Contentents |
  | :---: | --- |
  | /proc/cmdline | Options passed to the kernel by the boot loader at boot time, such as mounting the kernel as read-only. |
  | /proc/cpuinfo | Information about the processor, such as its type, make, model, and performance. |
  | /proc/devices | List of device drivers configured into the currently running kernel. |
  | /proc/filesystems | Filesystems configured into the kernel. |
  | /proc/interrupts | Shows which interrupts are in use, and how many of each there have been. |
  | /proc/ioports | Which I/O ports are in use at the moment. |
  | /proc/meminfo | Information about memory usage, both physical and swap. |
  | /proc/modules | Which kernel modules are loaded at the moment. |
  | /proc/net | Status information about network protocols. |
  | /proc/stat | Various statistics about the system, such as the number of page faults since the system was booted. |
  | /proc/uptime | The length of time the kernel has been running since boot and spent in idle mode (both in seconds). |
- สามารถหาข้อมูลเกี่ยวกับ kernel ได้ในไฟล์ /proc/version
  ```
  host-3@host-3-server$ cat /proc/version
  Linux version 5.15.0-91-generic (buildd@lcy02-amd64-045) (gcc (Ubuntu 11.4.0-1ubuntu1~22.04)) 11.4.0,
   GNU 1d (( GNU Bitnutils for Ubantu) 2.38)# 101-Ubuntu SMP Tue Nov 14 13:30:38 UTC 2023
  ```
  - 5 -- Kernel version
  - 15 -- Major revision
  - 0 -- Minor revision
  - 91 -- Bug fix
  - generic - บอกว่ากำลังใช้ Ubantu ที่เป็น Desktop version โดยหากเป็น Server version จะเป็นคำว่า 'server'
  







