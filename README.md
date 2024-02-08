# Host-3
Computer Organization and Operating System Assignment (Chapter: Host, Sec: 3)

## Overview :mag:
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
 $ lspci -v
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

| ID  | Name | Topic | Image |
| ------------- | --------------------------- | :-------------: | :-----------: |
| 65070008  | นางสาวกมลนิตย์ ธรรมชาติ  | Kernel | <img src="https://scontent.fbkk28-1.fna.fbcdn.net/v/t39.30808-6/426359464_1475576286636292_2307075857368261346_n.jpg?stp=cp6_dst-jpg_p180x540&_nc_cat=105&ccb=1-7&_nc_sid=3635dc&_nc_ohc=ClEWIRrpeMIAX-vlqYc&_nc_ht=scontent.fbkk28-1.fna&oh=00_AfDEFF-K0TOSfIDXQq_E61Bmg8-hWh7BJju6XA2O2pSY3g&oe=65C8C6F1" width="35%"> |
| 65070026  | นางสาวเกวลี ธนโชติชญานี  | Host Overview | <img src="https://private-user-images.githubusercontent.com/118044723/303320018-39416715-a1ca-4305-b6e8-638609a59a46.jpg?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MDczOTQxNDAsIm5iZiI6MTcwNzM5Mzg0MCwicGF0aCI6Ii8xMTgwNDQ3MjMvMzAzMzIwMDE4LTM5NDE2NzE1LWExY2EtNDMwNS1iNmU4LTYzODYwOWE1OWE0Ni5qcGc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjQwMjA4JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI0MDIwOFQxMjA0MDBaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1jYmViYWEzYjc5ZTBjZjI5OGNhYWEyZTAwNGFmM2UwNTExNDU2ZGUwNTAxZTcyNTA1OGE2NjZiYzg1MzI3YzU1JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZhY3Rvcl9pZD0wJmtleV9pZD0wJnJlcG9faWQ9MCJ9.GxNcpoK8cYD4yzN3gnSIM2MA9jK5V7E5GZcX7eZIV7c" width="35%"> |
| 65070113  | นายนพกร บุญมี  | Memory | <img src="https://github.com/aaomprt/Host-3/assets/117189340/891729e4-b890-4c68-8ae3-bc88cbd90e5d" width="35%"> |
| 65070131  | นางสาวปราณปรีญา เม่งมั่งมี  | Kernel | <img src="https://scontent.fbkk3-4.fna.fbcdn.net/v/t39.30808-1/357108356_6260830513993404_6867662345275536233_n.jpg?stp=dst-jpg_p320x320&_nc_cat=108&ccb=1-7&_nc_sid=5740b7&_nc_eui2=AeE80EGz3AZxG-4hQSqa8CPv13EjVCntvmjXcSNUKe2-aJtoXaAb9LTWeWh3jWBvlbhOJYQAyFBcKMZfPDlEP3m8&_nc_ohc=YabJ-qpm2wYAX8SQZGG&_nc_ht=scontent.fbkk3-4.fna&oh=00_AfDiuW7gOZ0MjkbfcwWLZ3aoRssuPImaqVbGtDO4L_1otw&oe=65CA83B7" width="35%"> |
| 65070132  | นางสาวปลายฟ้า พุ่มเจริญ  | Host Configuration | pic |
| 65070137  | นางสาวปานฤทัย ผิวสุข  | Host Configuration | <img src="https://scontent.fbkk22-4.fna.fbcdn.net/v/t39.30808-6/426748090_2045454635819086_4290629315869297157_n.jpg?_nc_cat=109&ccb=1-7&_nc_sid=dd5e9f&_nc_ohc=W7nj3MNRNMoAX9jqJ1A&_nc_ht=scontent.fbkk22-4.fna&oh=00_AfBVLSViEwyaxXeiqrINlAkeIqT2z1ABPY8Zh_LElID1nQ&oe=65CA476D" width="35%"> |
| 65070145  | นางสาวพรรณราย สุคง  | Input and Output Devices | <img src="https://cdn.discordapp.com/attachments/1147610510951452702/1205126934137274378/IMG_5969.jpg?ex=65d73ceb&is=65c4c7eb&hm=e397ffbe5401198e0b9ee96ff5e61ac199f0d567dda5dfad416d3ff123838a96&" width="35%"> |

## [Reference](https://github.com/aaomprt/Host-3/blob/main/references.md) :unlock:



