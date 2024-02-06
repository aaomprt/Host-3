# Host-3
Computer Organization and Operating System Assignment (Chapter: Host, Sec: 3)

## Overview
Host หมายถึง คอมพิวเตอร์หรือเซิร์ฟเวอร์ที่ทำหน้าที่ในเครือข่าย โดยประกอบด้วยการทำงานร่วมกันของ sub components เหล่านี้เพื่อให้ระบบทำงานได้ตามปกติ sub components ดังกล่าวได้แก่<br />
1. Host Configuration<br />
  - ทำหน้าที่จัดเก็บและจัดการข้อมูลในไฟล์ /etc/hosts เพื่อให้ host สามารถติดต่อและทำงานกับเครื่องอิ่นๆได้ตามที่ต้องการ อย่างมีประสิทธิภาพ <br /><br />
   ตัวอย่างคำสั่ง:<br />
   คำสั่งที่ใช้เพื่อดูว่าเนื้อหาภายในไฟล์ /etc/hosts มีกี่บรรทัด
  ```
  $ cat /etc/hosts
  ```
2. I/O Devices<br />
   - อุปกรณ์ I/O เป็นอุปกรณ์ที่รับข้อมูลเข้าระบบผ่าน คีย์บอร์ด, เมาส์ และส่งข้อมูลออกผ่านจอมอนิเตอร์ เป็นหลัก<br /><br />
   ตัวอย่างคำสั่ง:<br />
   คำสั่งเพื่อแสดงรายละเอียดของอุปกรณ๋ PCI ทั้งหมด
  ```
 # lspci -v
  ```
3. Kernel<br />
  - ส่วนสำคัญที่คอยดูแลบริหารทรัพยากรระบบ และติดต่อกับฮาร์ดแวร์ และซอฟแวร์ <br /><br />
  ตัวอย่างคำสั่ง:<br />
   `depmod [option]` หรือก็คือคำสั่งสร้างไฟล๋หรืออัปเดตไฟล์ใน kernel
  ```
  $ depmod -a
  ```
4. Memory<br />

## Members :space_invader:

| ID  | Name | Topic | Image
| ------------- | ------------- | ------------- | ------------- |
| 65070xxx  | Name  | topic | pic |
| 65070xxx  | Name  | topic | pic |
| 65070xxx  | Name  | topic | pic |
| 65070xxx  | Name  | topic | pic |
| 65070xxx  | Name  | topic | pic |
| 65070xxx  | Name  | topic | pic |
| 65070xxx  | Name  | topic | pic |
