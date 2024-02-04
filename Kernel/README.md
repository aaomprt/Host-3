--- kernel ---


------ครึ่งหลัง------------------

## Kernel Module Configuration
  - คำสั่ง **modprobe** สามารถใช้เพิ่มหรือลบโมดูลได้ โดยมีไฟล์ .conf ทั้งหมดภายในส่วนขยายไดเร็กทอรี /etc/modprobe.d สำหรับระบุตัวเลือกที่จำเป็นสำหรับโมดูลต่างๆ 
  - file configuration สามารถใช้สร้าง alias (ชื่อสำรองสำหรับโมดูล) หรือเปลี่ยนแปลงลักษณะการทำงานของ modprobe ตามความต้องการ ไฟล์ .conf อยู่ในไดเร็กทอรี /etc/modprobe.d และใน Linux เวอร์ชันเก่า จะอยู่ในไฟล์ /etc/modprobe.conf

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
- การสร้างชื่อแฝง (alias) สำหรับชื่อโมดูล สามารถสร้างfile .conf /etc/modprobe.d/ เช่น myalias.conf และ กำหนดผ่านโครงสร้าง alias [alias] [module name] ตัวอย่างด้านล่างเป็นการสร้าง alias mymod แทนชื่อโมดูลที่ยาวเกินไป
    ```
alias mymod really_long_module_name
  ```

