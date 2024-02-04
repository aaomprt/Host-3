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



