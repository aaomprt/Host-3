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
| -a | แสดง alias name ของ host ซึ่งถ้าไม่มีจะ return บรรทัดว่างออกมา |
| -A | แสดง FQDNs (Fully Qualified Domain Name) |
| -b | set the hostname |
| -d | แสดงชื่อ Domain ของ host |
| -f | แสดงชื่อ Domain แบบ Fully Qualified Domain Name (FQDN) |
| -F | set the hostname ที่ระบุในไฟล์ ซึ่งสามารถทำได้โดย superuser(root) เท่านั้น |
| -i | แสดง IP address ของ host ซึ่งจะใช้ได้เฉพาะในกรณีที่ hostname สามารถแก้ไขได้ |
| -I | แสดง IP address ของ host ซึ่งจะไม่ขึ้นอยู่กับความสามารถที่ hostname แก้ไขได้ |
| -s | แสดง hostname แบบย่อ ซึ่งจะอยู่ในส่วนก่อน period/dot(.) |
| -V | แสดง version ที่เกี่ยวกับ hostname |
