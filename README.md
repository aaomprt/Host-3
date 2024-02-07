# Host-3
Computer Organization and Operating System Assignment (Chapter: Host, Sec: 3)

## Overview
Host หมายถึง คอมพิวเตอร์หรือเซิร์ฟเวอร์ที่ทำหน้าที่ในเครือข่าย โดยประกอบด้วยการทำงานร่วมกันของ sub components เหล่านี้เพื่อให้ระบบทำงานได้ตามปกติ sub components ดังกล่าวได้แก่<br />
1. Host Configuration<br />
  - ทำหน้าที่จัดเก็บและจัดการข้อมูลในไฟล์ /etc/hosts เพื่อให้ host สามารถติดต่อและทำงานกับเครื่องอื่นๆได้ตามที่ต้องการ อย่างมีประสิทธิภาพ <br /><br />
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
  - ส่วนสำคัญที่คอยดูแล บริหารทรัพยากรของระบบ และติดต่อกับฮาร์ดแวร์ และซอฟแวร์ <br /><br />
  ตัวอย่างคำสั่ง:<br />
   `depmod [option]` หรือก็คือคำสั่งสร้างไฟล๋หรืออัปเดตไฟล์ใน kernel
  ```
  $ depmod -a
  ```
4. Memory<br />
 - มีหน้าที่ในการรับผิดชอบการเก็บข้อมูลที่ใช้ในการทำงานของระบบ  <br /><br />
 ตัวอย่างคำสั่ง:<br />
   คำสั่ง free ใช้ในการแสดงข้อมูลการใช้งาน memory
  ```
  $ free
  ```
## Topic :card_index_dividers:
- [Host Configuration](https://github.com/aaomprt/Host-3/tree/main/Host%20Configuration) :paperclip:
- [Input Output Devices](https://github.com/aaomprt/Host-3/tree/main/Input%20Output%20Devices) :keyboard:
- [Kernel](https://github.com/aaomprt/Host-3/tree/main/Kernel) :pushpin:
- [Memory](https://github.com/aaomprt/Host-3/tree/main/Memory) :floppy_disk:

## Members :space_invader:

| ID  | Name | Topic | Image
| ------------- | ------------- | ------------- | ------------- |
| 65070008  | นางสาวกมลนิตย์ ธรรมชาติ  | Kernel | pic |
| 65070026  | นางสาวเกวลี ธนโชติชญานี  | Host Overview | pic |
| 65070113  | นายนพกร บุญมี  | Memory | pic |
| 65070131  | นางสาวปราณปรีญา เม่งมั่งมี  | Kernel | pic |
| 65070132  | นางสาวปลายฟ้า พุ่มเจริญ  | Host Configuration | pic |
| 65070137  | นางสาวปานฤทัย ผิวสุข  | Host Configuration | pic |
| 65070145  | นางสาวพรรณราย สุคง  | Input and Output Devices | pic |

## [Reference](https://github.com/aaomprt/Host-3/blob/main/references.md) :unlock:
