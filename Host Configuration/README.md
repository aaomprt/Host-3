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
#### ตัวอย่างการใช้คำสั่ง hostname:
```
$ hostname -i
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
#### ตัวอย่างการใช้คำสั่ง timedatectl:
```
$ timedatectl set-ntp true
```
ซึ่งมี command ในการกำหนดค่าต่างๆ ดังนี้:
| Command | Description |
| ------- | ----------- |
| set-time [ time ] | Set the system clock to the specified time
| set-timezone [ timezone ] |  Set the system time zone to the specified value
| set-ntp [ true or false ] | add Network Time Protocol (NTP) synchronization to maintain the correct time automatically


| References |
| :---: |
|[Linkedin](https://www.linkedin.com/pulse/hosts-configuration-file-linux-razvan-alexandru-ionica) |


### 3. cd
เป็นคำสั่งที่ใช้ในการเข้าถึงหรือปลี่ยน Directory ปัจจุบันไปยัง Path นั้น คำสั่งนี้มีรูปแบบเป็น case sensitive ต้องพิมพ์ตัวอักษรเล็กใหญ่ให้ถูกต้องเท่านั้น ไม่เช่นนั้นจะมี error
   * การเข้าไปที่ Directory etc
     ### ตัวอย่างการใช้คำสั่ง cd:
     ```
     $ cd / etc
     ```
   * ย้อน Directory กลับขึ้นไปหนึ่งขั้น
     ### ตัวอย่างการใช้คำสั่ง cd:
     ```
     $ cd ..
     ```


### 4. cp
ใช้เพื่อ copy file หรือ directory ที่เราสนใจ ไปยัง directory เป้าหมาย หรือ copy สร้างเป็น file ใหม่ตามที่เราต้องการ
### Syntax:
```
cp [files name / directory] [Destination]
```

### 5. grep
คำสั่งสำหรับค้นหาคำ ตามเงื่อนไขที่ต้องการ
### ตัวอย่างการใช้คำสั่ง cd:
```
$ cd
```

### 6. ll



### 7. vi


### 8. cat
ใช้รวมข้อมูล file รวมถึงแสดงผลข้อมูลออกมาในรูปแบบ tex

### 9. touch

### 10. mkdir

### 11. NTP
เป็นการสั่งให้เครื่อง Host ซึ่งทำหน้าที่เป็น NTP client ใช้เวลาจากเซิร์ฟเวอร์ NTP โดยสามารถปรับปรุงเวลาได้อัตโนมัติ ทำได้โดยการติดตั้งและกำหนดค่าแพ็กเกจ ntp และทำการกำหนดค่าในไฟล์ `/etc/ntp.conf`
* Update the package:
```
sudo apt update
```
* Install the NTP package:
```
sudo apt install ntp
```
* config NTP ได้ในไฟล์ /etc/ntp.conf โดยสามารถเปิดผ่านคำสั่ง:
```
sudo nano /etc/ntp.conf
```
* Restart the NTP เพื่อ apply ไฟล์ที่เรา config ไป
```
sudo systemctl restart ntp
```
* ตรวจสอบว่า NTP สามารถทำงานได้ถูกต้อง โดยใช้คำสั่ง:
```
sudo systemctl status ntp
```

### 12. lshw

### 13. lscpu
