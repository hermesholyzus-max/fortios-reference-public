# คู่มือใช้งาน FortiOS Reference สำหรับ Agent

เวอร์ชันเอกสาร: FortiOS 7.4.13
ขอบเขต: คู่มือทั่วไปสำหรับ FortiGate/FortiOS 7.4.13 ทุกโมเดล

---

## 1. วัตถุประสงค์

โฟลเดอร์นี้เป็นคลังอ้างอิงสำหรับการตรวจสอบ วางแผน และปรับแต่ง FortiGate/FortiOS โดยใช้เอกสารทางการของ Fortinet ร่วมกับ live configuration ของอุปกรณ์จริง

ห้ามโหลดหรือส่ง Admin Guide ทั้งเล่มเข้า model ในครั้งเดียว ให้ค้นหาและอ่านเฉพาะหัวข้อที่เกี่ยวข้องกับงานปัจจุบัน เพื่อประหยัด token และลดความสับสนจากข้อมูลจำนวนมาก

---

## 2. ตำแหน่งคลังเอกสาร

Google Drive folder:

```text
https://drive.google.com/drive/folders/1rgjbKhBiBb9hg9gXX5-nIYm_MRfGRVjV
```

โครงสร้างจริงของลิงก์นี้คือ: เมื่อเปิดลิงก์ Google Drive จะเข้าสู่โฟลเดอร์ `fortios-reference` โดยตรง ไม่ได้มีชั้น `FortiOS Reference/FortiOS 7.4.13` ซ้อนอยู่ด้านบน

```text
fortios-reference/
├── START_HERE.md
├── AGENT_USAGE.md
├── HERMES_AGENT_PROMPT.md
├── SKILL.md
├── source/
│   └── FortiOS-7.4.13-Administration_Guide.pdf
├── references/
│   ├── index.md
│   ├── getting-started.txt
│   ├── getting-started.pdf
│   ├── network.txt
│   ├── network.pdf
│   ├── policy-and-objects.txt
│   ├── policy-and-objects.pdf
│   ├── security-profiles.txt
│   ├── security-profiles.pdf
│   ├── ipsec-vpn.txt
│   ├── ipsec-vpn.pdf
│   ├── ssl-vpn.txt
│   ├── ssl-vpn.pdf
│   ├── system.txt
│   ├── system.pdf
│   ├── troubleshooting.txt
│   └── troubleshooting.pdf
└── scripts/
    └── build_reference.py
```

ให้ถือว่าโฟลเดอร์ที่เปิดจาก URL เป็น root ของ reference และใช้ path ที่แสดงด้านบนโดยตรง

`*.txt` ใช้สำหรับค้นหาและอ่านเฉพาะส่วนที่จำเป็น ส่วน `*.pdf` ใช้เมื่อต้องดูภาพหน้าจอ GUI ตาราง หรือ layout ต้นฉบับ

---

## 3. ขั้นตอนเริ่มต้นทุกงาน

1. อ่าน `references/index.md`
2. ระบุหัวข้อที่เกี่ยวข้องกับงาน
3. ค้นเฉพาะไฟล์ `.txt` ของหัวข้อนั้น
4. บันทึกเลขหน้า PDF ที่พบในคำตอบหรือแผนงาน
5. ตรวจสอบ live configuration ของ FortiGate ก่อนเสนอหรือใช้คำสั่ง
6. เปรียบเทียบคำแนะนำจากคู่มือกับรุ่นอุปกรณ์และ topology จริง

ห้ามเริ่มจากการอ่าน `source/FortiOS-7.4.13-Administration_Guide.pdf` ทั้งเล่ม เว้นแต่ต้องทำงานวิจัยเฉพาะด้านจริง ๆ

---

## 4. ตารางเลือกไฟล์อ้างอิง

| งาน | ไฟล์ที่ต้องอ่าน |
|---|---|
| ตั้งค่า interface, hardware switch, VLAN | `references/network.txt` |
| DHCP server/relay | `references/network.txt` |
| Static route, policy route, routing diagnosis | `references/network.txt` และ `references/troubleshooting.txt` |
| Firewall policy, NAT, address object, service | `references/policy-and-objects.txt` |
| Antivirus, Web Filter, DNS Filter, IPS | `references/security-profiles.txt` |
| IPsec site-to-site หรือ dial-up VPN | `references/ipsec-vpn.txt` |
| SSL VPN | `references/ssl-vpn.txt` |
| Administrator, SSH key, HTTPS port, backup, HA | `references/system.txt` |
| Packet capture, debug flow, session, logs | `references/troubleshooting.txt` |
| ขั้นตอน setup เริ่มต้น | `references/getting-started.txt` |

---

## 5. วิธีค้นหาเอกสาร

ค้นหาคำสำคัญในไฟล์ text เฉพาะหัวข้อ เช่น:

```bash
rg -n -i "VLAN|vlanid|config system interface" references/network.txt
rg -n -i "DHCP|ip-range|default-gateway" references/network.txt
rg -n -i "firewall policy|srcintf|dstintf|set nat" references/policy-and-objects.txt
rg -n -i "ssh-public-key|Public key SSH access|backup" references/system.txt
rg -n -i "debug flow|packet capture|routing table" references/troubleshooting.txt
```

ในแต่ละไฟล์จะมีตัวคั่นหน้าในรูปแบบ:

```text
===== FortiOS 7.4.13 PDF page 445 =====
```

เมื่อพบข้อมูลสำคัญ ให้บันทึกเลขหน้าไว้เพื่อให้ agent หรือผู้ดูแลตรวจสอบย้อนกลับได้

---

## 6. หลักการใช้คู่มือร่วมกับ live configuration

ลำดับความสำคัญของข้อมูล:

1. Live configuration และสถานะจริงของ FortiGate
2. คู่มือ FortiOS 7.4.13
3. ตัวอย่าง configuration ในคู่มือ
4. ความรู้ทั่วไปจาก model

หากคู่มือกับ live config ขัดแย้งกัน ให้หยุดและตรวจสอบสาเหตุ เช่น:

- รุ่น FortiGate ต่างกัน
- FortiOS patch ต่างกัน
- VDOM mode ต่างกัน
- interface เป็น hardware switch หรือ physical port ต่างกัน
- ค่า default ของอุปกรณ์ต่างกัน
- topology จริงไม่เหมือนตัวอย่างในคู่มือ

ห้าม copy configuration ทั้งไฟล์ข้ามรุ่นหรือข้าม topology โดยไม่ตรวจสอบ hardware-specific settings, interface layout, VDOM, certificates, secrets และ routing ก่อน

---

## 7. การปรับใช้กับอุปกรณ์จริง

คู่มือนี้เป็น reference ทั่วไป ไม่ใช่ live configuration ของอุปกรณ์ใดอุปกรณ์หนึ่ง ก่อนเสนอหรือใช้คำสั่งต้องตรวจสอบอย่างน้อย:

- model และ serial
- FortiOS version/build และ VDOM mode
- interface หรือ hardware-switch layout
- WAN/LAN topology และ addressing plan
- certificates, secrets และ authentication dependencies
- live interface, route, DHCP และ policy configuration ที่เกี่ยวข้อง

---

## 8. ขั้นตอนก่อนเปลี่ยน configuration

ก่อน state-changing operation ทุกครั้ง:

1. ยืนยันอุปกรณ์และ VDOM ที่กำลังเชื่อมต่อ
2. ตรวจ hostname, serial/model และ FortiOS version
3. อ่าน interface, route, DHCP และ policy ที่เกี่ยวข้อง
4. สำรอง config หรือยืนยัน rollback path
5. ระบุสิ่งที่จะเปลี่ยนและสิ่งที่ห้ามเปลี่ยน
6. ทำการเปลี่ยนแปลงให้น้อยที่สุด
7. อ่าน object ที่แก้กลับทันที
8. ทดสอบ management access และ forwarding behavior
9. รายงานสิ่งที่เปลี่ยน สิ่งที่ตรวจแล้ว และสิ่งที่ยังไม่ได้ทดสอบ

ห้ามรวมการเปลี่ยน WAN, VLAN, DHCP, route และ firewall policy จำนวนมากในคำสั่งเดียวโดยไม่มีจุดตรวจสอบกลาง

---

## 9. รูปแบบรายงานที่ต้องใช้

ทุกงาน FortiGate ควรรายงานตามรูปแบบนี้:

```text
อุปกรณ์:
VDOM:
FortiOS:

เปลี่ยนแปลงแล้ว:
- ...

ตรวจสอบแล้ว:
- ...

ผลทดสอบ:
- ...

ยังไม่ได้ทดสอบ:
- ...

ความเสี่ยง/ข้อจำกัด:
- ...

แหล่งอ้างอิง:
- FortiOS PDF page ...
- references/<topic>.txt
```

ห้ามรายงานว่า internet, VPN หรือ client forwarding ใช้งานได้ เพียงเพราะ FortiGate เอง ping ได้ ต้องทดสอบจาก client หรือใช้ flow/packet evidence ให้ตรงกับเส้นทางจริง

---

## 10. การจัดการข้อมูลลับ

- ห้ามใส่รหัสผ่าน, private key, PSK, token, certificate private key หรือ API secret ลงใน manual
- ห้ามส่งข้อมูลลับเข้า Google Drive reference folder
- หากพบข้อมูลลับใน config ที่จะส่งต่อ ให้ลบหรือแทนด้วย `<REDACTED>` ก่อน
- Public SSH key สามารถบันทึกเป็นข้อมูลอ้างอิงได้ แต่ private key ห้ามอัปโหลด
- ใช้ credential vault หรือวิธี authentication ที่ปลอดภัยแทนการเขียนรหัสผ่านลงเอกสาร

---

## 11. การอัปเดตเอกสาร

เมื่อ FortiOS version เปลี่ยน:

1. สร้างโฟลเดอร์ version ใหม่ เช่น `FortiOS 7.6.x`
2. ดาวน์โหลด Admin Guide ของ version นั้นใหม่
3. สร้าง `references/index.md` ใหม่
4. แยก topic PDF/text ใหม่
5. ห้ามเขียนทับ reference ของ 7.4.13
6. ระบุ source URL, วันที่ดาวน์โหลด และจำนวนหน้า
7. ตรวจสอบคำสั่งที่ใช้กับอุปกรณ์จริงก่อนใช้งาน

เมื่อมีการแก้ manual ให้เพิ่มวันที่และเหตุผลของการแก้ไขใน changelog

---

## 12. คำสั่งเริ่มงานที่แนะนำสำหรับ agent

```text
ใช้ FortiOS Reference จาก Google Drive นี้เป็นข้อมูลอ้างอิง
อ่าน references/index.md ก่อน
งานนี้เกี่ยวข้องกับ <หัวข้อ>
ให้อ่านเฉพาะ references/<topic>.txt
ตรวจ live configuration ของอุปกรณ์ก่อนเสนอคำสั่ง
อย่าเปลี่ยน config จนกว่าจะสรุปความเสี่ยงและจุด rollback
อ้างอิงเลขหน้า PDF ในรายงาน
```

---

## 13. หลักสำคัญที่สุด

คู่มือนี้เป็น reference ไม่ใช่คำสั่งให้ทำงานแบบอัตโนมัติ

**Live state ต้องตรวจสอบก่อนเสมอ และทุกการเปลี่ยนแปลงต้องมี verification หลังทำทันที**
