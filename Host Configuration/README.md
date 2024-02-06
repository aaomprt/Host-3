# Host Configuration

## หน้าที่และหลักการทำงานบน Linux
* ผักหวานใส่ตรงนี้ได้เบยนะงับ
* หลักการทำงานหลักๆของ Host Configuration คือ การจับคู่ (map) domain names หรือ hostnames กับ IP addresses ซึ่งจะสามารถเปลี่ยนเส้นทางการรับส่งข้อมูลไปยัง IP address ที่ต้องการได้ โดย linux จะทำการอ่านไฟล์ /etc/hosts เพื่อให้เข้าใจการกำหนดค่าและการตั้งค่าของเครื่อง host

## Command
### 1. hostname
ชื่อของเครื่อง Host ซึ่งสามารถกำหนดหรือแก้ไขได้ในไฟล์ `/etc/hostname` หรือผ่านคำสั่ง `hostname`
#### Syntax:
```
hostname [options] [new_hostname]
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
การกำหนดค่าวันที่ เวลา และโซนเวลาของเครื่อง Host เพื่อให้เครื่อง Host สามารถแสดงเวลาให้ถูกต้อง ซึ่งสามารถกำหนดได้ผ่านคำสั่ง `date`, `timedatectl` หรือผ่านการแก้ไขไฟล์ `/etc/timezone` และ `/etc/localtime`

| References |
| :---: |
|[Linkedin](https://www.linkedin.com/pulse/hosts-configuration-file-linux-razvan-alexandru-ionica) |
