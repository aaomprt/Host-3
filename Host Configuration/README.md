# Host Configuration

* หลักการทำงานหลักๆของ Host Configuration คือ การจับคู่ (map) domain names หรือ hostnames กับ IP addresses ซึ่งจะสามารถเปลี่ยนเส้นทางการรับส่งข้อมูลไปยัง IP address ที่ต้องการได้ โดย linux จะทำการอ่านไฟล์ /etc/hosts เพื่อให้เข้าใจการกำหนดค่าและการตั้งค่าของเครื่อง host

## Command
### 1. hostname
ชื่อของเครื่อง Host ซึ่งสามารถกำหนดหรือแก้ไขได้ในไฟล์ `/etc/hostname` หรือผ่านคำสั่ง `hostname`
#### Syntax
```
hostname [options] [new_hostname]
```
| Option        | Description   |
| ------------- |:-------------:|
| -a      | right-aligned |
| -A      | centered      |
| zebra stripes | are neat      |
