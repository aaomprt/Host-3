# 🔧 Host Configuration 🔧

### หน้าที่และหลักการทำงานบน Linux 🖥️
* **หน้าที่หลักของ Host Configuration บนระบบปฏิบัติการ Linux** คือ การจัดเก็บและบริหารจัดการข้อมูลในไฟล์ `/etc/hosts` เพื่อให้เครื่องคอมพิวเตอร์สามารถระบุและติดต่อกับเครื่องอื่น ๆ ในเครือข่ายได้อย่างมีประสิทธิภาพและมีความน่าเชื่อถือ 
* **หลักการทำงานของ Host Configuration** คือ การจับคู่ (map) domain names หรือ hostnames กับ IP addresses ซึ่งจะสามารถเปลี่ยนเส้นทางการรับส่งข้อมูลไปยัง IP address ที่ต้องการได้ โดย linux จะทำการอ่านไฟล์ `/etc/hosts` เพื่อให้เข้าใจการกำหนดค่าและการตั้งค่าของเครื่อง host


## Command 📁

### 1. hostname 📝
ชื่อของเครื่อง Host ซึ่งสามารถกำหนดหรือแก้ไขได้ในไฟล์ `/etc/hostname` หรือผ่านคำสั่ง `hostname`
#### Syntax:
```
hostname [ options ] [ new_hostname ]
```
#### ตัวอย่างการใช้คำสั่ง hostname:
```
$ hostname -i
```
#### ตัวอย่าง option มีดังนี้:
| Option        | Description   |
| :-----------: | ------------- |
| -a | แสดง alias name ของ host |
| -A | แสดงทุก (Fully Qualified Domain Name) ของ computer |
| -b | ตั้งชื่อ hostname |
| -d | แสดงชื่อ DNS domain |
| -f | แสดง FQDN |
| -F | ตรวจสอบไฟล์เพื่อ recover และแสดง hostname |
| -i | แสดง IP address ของ computer |
| -I | แสดง IP address ทั้งหมดของ computer |
| -s | แสดง version ของ hostname แบบย่อ |


### 2. Date, Time, Time Zone ⏲️
การกำหนดค่าวันที่ เวลา และโซนเวลาของเครื่อง Host เพื่อให้เครื่อง Host สามารถแสดงเวลาให้ถูกต้อง ซึ่งสามารถกำหนดได้ผ่านคำสั่ง `timedatectl` หรือผ่านการแก้ไขไฟล์ `/etc/timezone` และ `/etc/localtime`
#### Syntax:
```
 timedatectl [ OPTIONS ]
```
#### ตัวอย่างการใช้คำสั่ง timedatectl:
```
$ timedatectl set-ntp true
```
#### ซึ่งมี command ในการกำหนดค่าต่างๆ ดังนี้:
| Command | Description |
| ------- | ----------- |
| set-time [ time ] | ตั้งเวลา clock ตามที่กำหนด
| set-timezone [ timezone ] |  ตั้ง time zone ตามที่กำหนด
| set-ntp [ true or false ] | เพิ่ม Network Time Protocol (NTP) synchronization เพื่อรักษาเวลาให้ถูกต้องอัตโนมัติ


### 3. cd 📄
เป็นคำสั่งที่ใช้ในการเข้าถึงหรือปลี่ยน Directory ปัจจุบันไปยัง Path นั้น คำสั่งนี้มีรูปแบบเป็น case sensitive ต้องพิมพ์ตัวอักษรเล็กใหญ่ให้ถูกต้องเท่านั้น ไม่เช่นนั้นจะมี error
   * การเข้าไปที่ Directory etc
     #### ตัวอย่างการใช้คำสั่ง cd:
     ```
     $ cd / etc
     ```
   * ย้อน Directory กลับขึ้นไปหนึ่งขั้น
     #### ตัวอย่างการใช้คำสั่ง cd:
     ```
     $ cd ..
     ```


### 4. cp 📄
ใช้เพื่อ copy file หรือ directory ที่เราสนใจ ไปยัง directory เป้าหมาย หรือ copy สร้างเป็น file ใหม่ตามที่เราต้องการ
#### Syntax:
```
cp [ files name / directory ] [ Destination ]
```

### 5. grep 📄
ใช้อ่านไฟล์ที่เราต้องการค้นหาทีละบรรทัด แล้วดูว่าตรง (match) กับคำหรือรูปแบบที่เราต้องการค้นหาหรือไม่ 
#### Syntax:
```
$ grep [ OPTION ] [ FILE ]
```
#### Option มีดังนี้:
| Option | Description |
| :----: | ----------- |
| -c | แสดงเพียงหนึ่งครั้งต่อไฟล์ของบรรทัดที่เลือก |
| -h | ลบคำนำหน้าออกจากชื่อไฟล์ Unix ในเอาต์พุต |
| -i | จะไม่แยกความแตกต่างระหว่างตัวพิมพ์ใหญ่และตัวพิมพ์เล็ก |
| -l | แสดงเฉพาะชื่อไฟล์ที่มีบรรทัดที่เลือก |
| -n | แสดงเลขบรรทัด |
| -v | ไม่แสดงบรรทัดที่มีคำที่ต้องการ |
| -E | เราสามารถระบุรูปแบบ (pattern) ในการค้นหา |
| -w | บังคับให้ค้นหาเฉพาะคำที่เจาะจง |
| -r | ค้นหาไดเรกทอรีแบบวนซ้ำ |
| -R | เหมือน -r แต่ทำตามลิงก์สัญลักษณ์ทั้งหมด |
| -color | แสดงรูปแบบการจับคู่สี |
| -e exp | ระบุexpressionในการค้นหาเพิ่มเติม |
| -f file | ระบุไฟล์ที่มี expression การค้นหา |
| -o | แสดงข้อความที่ตรงกับเงื่อนไขเท่านั้น |
| -A n | แสดงบรรทัดที่ตรงกับเงื่อนไขพร้อมแสดง n บรรทัดหลังจากบรรทัดผลลัพท์ |
| -B n | แสดงบรรทัดที่ตรงกับเงื่อนไขพร้อมมแสดง n บรรทัดก่อนบรรทัดผลลัพท์ |
| -C n | แสดงบรรทัดที่ตรงกับเงื่อนไขพร้อมบรรทัดที่อยู่ก่อน n บรรทัดทั้งก่อนและหลังบรรทัดผลลัพท์ |


### 6. ll 📄
คำสั่งสำหรับแสดงไฟล์หรือโฟลเดอร์ภายในไดเร็กทอรี (เป็น alias ของ ls) หากต้องการให้เรียงไฟล์ปัจจุบันไปยังอดีต สามารถเพิ่ม `-th` ต่อท้าย
#### syntax
```
$ ll
```
หรือ
```
$ ll -th
```

### 7. vi 📄
VI เป็น Editor โปรแกรม ที่ติดตั้งมาบน Linux Server หรือ FreeBSD Server ซึ่งสามารถใช้สร้างไฟล์ แก้ไขไฟล์ได้ทันที จะมี Mode การทำงานอยู่ 2 โหมดหลักด้วยกัน คือ **Mode Command** และ **Mode Editor**

*เริ่มต้นการใช้งาน vi ได้โดยใช้คำสั่งตาม syntax ต่อไปนี้
#### syntax
```
$ vi (filename)
```
* ตัวอย่างคำสั่งที่ใช้ในการสร้างไฟล์:
  ```
  $ vi test.txt
  ```
* คำสั่งเขียนหรือแทรกข้อมูลลง file
  #### มีดังนี้:
| vi Editor Command | Description |
| :----: | ----------- |
| i | แทรกข้อมูลก่อน cursor |
| a | เพิ่มข้อมูลหลัง cursor |
 | A | เพิ่มข้อมูลท้ายบรรทัด |
 | I |  แทรกข้อมูลหน้าบรรทัด |
 | o | แทรกบรรทัดถัดไปของ cursor |
 | O | แทรกบรรถัดกก่อน cursor |
 | rx | เปลี่ยนตัวอักษรทับ 1 ตัว |
 | R | เปลี่ยนตัวอักษรทับหลายๆตัว |
 
* คำสั่งจัดการ file
#### มีดังนี้:
| vi Editor Command | Description |
| :----: | ----------- |
| :w | save file |
| :wq | save file และออกจาก vi |
| :q | ออกจาก vi ถ้าไม่มีการแก้ไขข้อมูล |
| :q! | ออกจาก vi โดยไม่สนว่าข้อมูลมีการแก้ไขหรือไม่ |
| :e name | เปลี่ยนชื่อ file |
| :e! | เอา save file version ล่าสุดกลับมา |
| e + name |  โหลด file เพื่อแก้ไข และเลือน cursor ไปบรรทัดสุดท้าย |
| :e +n name	 |   โหลด file เพื่อแก้ไข และเลือน cursor ไปบรรทัด n |
| :e # |  แก้ไข file อันใหม่ |
| ^^ |  เหมือน  :e # |
| :w name | save ข้อมูลลง file ใหม่ |
| :w! name |  save ข้อมูลทับลง file เดิม |
 
### 8. cat 📄
ใช้รวมข้อมูล file รวมถึงแสดงผลข้อมูลออกมาในรูปแบบ text
#### Syntax:
```
$ cat [ OPTION ] [ FILE ]
```
* ตัวอย่างการใช้คำสั่งในการแสดงข้อมูลในแฟ้ม `/etc/passwd`
```
$ cat /etc/passwd
```

#### มี command ที่ใช้ดังนี้:
| Command | Description |
| ------- | ----------- |
| cat > [fileName] | To create a file.
| cat [oldfile] > [newfile] | To copy content from older to new file.
| cat [file1 file2 and so on] > [new file name] | To concatenate contents of multiple files into one.
| cat -n/cat -b [fileName]	| To display line numbers.
| cat -e [fileName] | To display $ character at the end of each line.
| cat [fileName] <<EOF | Used as page end marker.

### 9. touch 📄
เป็นคำสั่งที่ใช้ในการเปลี่ยนแปลง file timestamps รวมถึงสามารถสร้าง file เปล่าได้
#### Syntax:
```
$ touch [ OPTION ] file_name
```
 
### 10. mkdir 📄
คำสั่งใช้สำหรับสร้าง Directory
#### Syntax:
```
$ mkdir <dirname> 
```

### 11. NTP 📄
เป็นการสั่งให้เครื่อง Host ซึ่งทำหน้าที่เป็น NTP client ใช้เวลาจากเซิร์ฟเวอร์ NTP โดยสามารถปรับปรุงเวลาได้อัตโนมัติ ทำได้โดยการติดตั้งและกำหนดค่าแพ็กเกจ ntp และทำการกำหนดค่าในไฟล์ `/etc/ntp.conf`
* Update the package:
  ```
  $ sudo apt update
  ```
* Install the NTP package:
  ```
  $ sudo apt install ntp
  ```
* config NTP ได้ในไฟล์ `/etc/ntp.conf` โดยสามารถเปิดผ่านคำสั่ง:
  ```
  $ sudo nano /etc/ntp.conf
  ```
* Restart the NTP เพื่อ apply ไฟล์ที่เรา config ไป
  ```
  $ sudo systemctl restart ntp
  ```
* ตรวจสอบว่า NTP สามารถทำงานได้ถูกต้อง โดยใช้คำสั่ง:
  ```
  $ sudo systemctl status ntp
  ```

### 12. lshw 📄
ใช้แสดงรายละเอียดเกี่ยวกับฮาร์ดแวร์ของเครื่อง Host เช่น CPU, RAM, และอุปกรณ์อื่นๆ โดยสามารถติดตั้งได้ผ่านการใช้คำสั่ง `sudo apt install lshw` และใช้คำสั่ง `lshw` เพื่อแสดงข้อมูล

#### Syntax:
```
lshw [ -format ] [ -options ]
```
#### format มีดังนี้:
| Format | Description |
| :----: | ----------- |
| -html | แสดงฮาร์ดแวร์ แบบ HTML tree |
| -xml | แสดงฮาร์ดแวร์ แบบ XML tree |
| -short | แสดง paths ฮาร์ดแวร์ |
| -businfo | แสดง bus information |
#### ตัวอย่างการใช้คำสั่ง lshw with format:
```
$ sudo lshw -short
```
#### Option มีดังนี้:
| Option | Description |
| :----: | ----------- |
| -class | แสดง hardware บางประเภทเท่านั้น |
| -disable, -enable | เปิดหรือปิด test เช่น pci, isapnp, cpuid, usb, network, etc. |
| -quiet | ไม่ต้องการให้แสดงสถานะ (status) |
| -sanitize | output โดยไม่ให้แสดง sensitive information |
| -numeric | แสดง ID สำหรับ PCI, USB, etc |
| -version | แสดง version ของ lshw |
| -help | แสดงข้อมูลคำสั่งที่เกี่ยวข้อง |
#### ตัวอย่างการใช้คำสั่ง lshw with option:
```
$ sudo lshw -sanitize
```

### 13. lscpu 📄
แสดงข้อมูลเกี่ยวกับ CPU ของเครื่อง Host เช่น ยี่ห้อ, รุ่น, ความเร็ว และคุณสมบัติอื่นๆ โดยสามารถเรียกใช้ได้โดยใช้คำสั่ง `lscpu`

#### Syntax:
```
lscpu [ options ]
```
| Option | Description |
| :----: | ----------- |
| -e | CPU information in human-readable format |
| -p | Optimizes the command output for easy parsing |
| -c | Limits the output to offline CPUs |
| -b | Allows the output to only online CPUs |
| -a | Includes online and offline CPU lines in the output |
| -x | Uses hexadecimal masks for CPU sets |
| -J | Uses JSON output format for the default summary or extended output |
| -C | Displays details about CPU caches |
| -B | Shows the sizes in bytes rather than in a human-readable format |
| --output-all | Prints all available columns |
| --hierarchic[=when] | Uses subsections in summary output |
| -s | Gathers CPU info for a Linux instance different from the instance from which the lscpu command is issued |
| -y | Displays physical IDs for all columns with topology elements (core, socket, etc.) |
#### ตัวอย่างการใช้คำสั่ง lscpu:
```
$ lscpu -e
```
