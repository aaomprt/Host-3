# Host Configuration

## หน้าที่และหลักการทำงานบน Linux
* หน้าที่หลักของ Host Configuration บนระบบปฏิบัติการ Linux คือการจัดเก็บและบริหารจัดการข้อมูลในไฟล์ /etc/hosts เพื่อให้เครื่องคอมพิวเตอร์สามารถระบุและติดต่อกับเครื่องอื่น ๆ ในเครือข่ายได้อย่างมีประสิทธิภาพและมีความน่าเชื่อถือ 
* หลักการทำงานหลักๆของ Host Configuration คือ การจับคู่ (map) domain names หรือ hostnames กับ IP addresses ซึ่งจะสามารถเปลี่ยนเส้นทางการรับส่งข้อมูลไปยัง IP address ที่ต้องการได้ โดย linux จะทำการอ่านไฟล์ /etc/hosts เพื่อให้เข้าใจการกำหนดค่าและการตั้งค่าของเครื่อง host

## Command

### 1. hostname
ชื่อของเครื่อง Host ซึ่งสามารถกำหนดหรือแก้ไขได้ในไฟล์ `/etc/hostname` หรือผ่านคำสั่ง `hostname`
#### Syntax:
```
hostname [ options ] [ new_hostname ]
```
โดยในส่วนของ option มีดังนี้:
| Option        | Description   |
| :-----------: | ------------- |
| -a | Displays the alias name of the host |
| -A | Displays every FQDN (Fully Qualified Domain Name) of the computer |
| -b | Always set a hostname |
| -d | Display DNS domain name |
| -f | Display the FQDN |
| -F | heck a file to recover and display the hostname |
| -i | Display the computer’s IP address |
| -I | Display all of the computer’s network addresses |
| -s | Display the short version of the hostname |
| -V | Expand all output to verbose |

### 2. Date, Time, Time Zone
การกำหนดค่าวันที่ เวลา และโซนเวลาของเครื่อง Host เพื่อให้เครื่อง Host สามารถแสดงเวลาให้ถูกต้อง ซึ่งสามารถกำหนดได้ผ่านคำสั่ง `timedatectl` หรือผ่านการแก้ไขไฟล์ `/etc/timezone` และ `/etc/localtime`
#### Syntax:
```
 timedatectl [ OPTIONS ]
```
ซึ่งมี command ในการกำหนดค่าต่างๆ ดังนี้:
| command | Description |
| ------- | ----------- |
| set-time [ time ] | Set the system clock to the specified time
| set-timezone [ timezone ] |  Set the system time zone to the specified value
| set-ntp [ true or false ] | add Network Time Protocol (NTP) synchronization to maintain the correct time automatically


| References |
| :---: |
|[Linkedin](https://www.linkedin.com/pulse/hosts-configuration-file-linux-razvan-alexandru-ionica) |

### 3. cd
เป็นคำสั่งที่ใช้ในการเข้าถึงหรือปลี่ยน Directory ปัจจุบันไปยัง Path นั้น
### ตัวอย่างการใช้คำสั่ง cd:
```
$ cd
```

### 4. cp
คำสั่งสำหรับสำเนาไฟล์หรือโฟล์เดอร์ไปยัง path อื่นๆ
### ตัวอย่างการใช้คำสั่ง cd:
```
$ cd
```

### 5. grep
คำสั่งสำหรับค้นหาคำ ตามเงื่อนไขที่ต้องการ
### ตัวอย่างการใช้คำสั่ง cd:
```
$ cd
```
