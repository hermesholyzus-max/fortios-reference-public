# Agent Access Guide: FortiOS 7.4.13 Reference

## Purpose

เอกสารนี้เป็นขั้นตอนสำหรับ agent ที่ต้องการอ่านคู่มือ configuration ทั่วไปของ FortiOS 7.4.13

คู่มือนี้ใช้กับ FortiGate ได้หลายโมเดล ไม่ได้จัดทำเฉพาะสำหรับรุ่นใดรุ่นหนึ่ง

## Google Drive Reference

เปิดโฟลเดอร์นี้โดยตรง:

```text
https://drive.google.com/drive/folders/1rgjbKhBiBb9hg9gXX5-nIYm_MRfGRVjV
```

สิทธิ์การเข้าถึงที่ตั้งไว้:

- Anyone with the link
- Viewer / อ่านอย่างเดียว
- ไม่ต้องใช้ GitHub login

หาก Google Drive แสดงหน้า login หรือ Access denied ให้หยุดและแจ้งผู้ใช้ทันที ห้ามเดาเนื้อหาคู่มือจากความจำ

## Reading Order

อ่านไฟล์ตามลำดับนี้:

1. `START_HERE.md`
2. `HERMES_AGENT_PROMPT.md`
3. `AGENT_USAGE.md`
4. `references/index.md`

หลังจากนั้นให้อ่านเฉพาะ topic `.txt` ที่เกี่ยวข้องกับงาน ห้ามโหลด Administration Guide PDF ทั้งเล่มโดยไม่จำเป็น

## Topic Selection

ใช้ไฟล์อ้างอิงตามหัวข้องาน:

- เริ่มต้นใช้งาน: `references/getting-started.txt`
- Interface, VLAN, routing, DHCP: `references/network.txt`
- Firewall policy และ objects: `references/policy-and-objects.txt`
- Security profiles: `references/security-profiles.txt`
- IPsec VPN: `references/ipsec-vpn.txt`
- SSL VPN: `references/ssl-vpn.txt`
- System, administrator, backup: `references/system.txt`
- Debug, packet capture, troubleshooting: `references/troubleshooting.txt`

ใช้ไฟล์ `.pdf` ของ topic เดียวกันเมื่อจำเป็นต้องดู screenshot, ตาราง หรือ layout ของ GUI

## Mandatory Safety Checks

ก่อนสร้างคำสั่งหรือเสนอการเปลี่ยนแปลง configuration จริง ต้องตรวจสอบข้อมูล live ก่อนเสมอ:

- FortiGate model
- Serial number
- FortiOS version และ build
- VDOM
- Interface layout
- Current topology
- Existing configuration
- Dependencies ของ policy, object, route และ VPN

ห้ามคัดลอก configuration จาก FortiGate รุ่นหนึ่งไปใช้กับอีกรุ่นโดยตรง เพราะชื่อ interface, ความสามารถ และโครงสร้างอาจแตกต่างกัน

สำหรับงานที่มีผลต่อระบบ:

1. อ่าน configuration ปัจจุบันก่อน
2. อธิบายผลกระทบและจุดที่ต้องตรวจ
3. เสนอคำสั่งแบบปลอดภัยและ reversible ก่อน
4. ขอการยืนยันก่อนคำสั่งที่มีความเสี่ยง
5. ตรวจสอบผลหลังเปลี่ยนแปลง

## Prohibited Content

ห้ามใส่หรือส่งต่อข้อมูลต่อไปนี้ใน prompt, repository, Google Drive reference หรือคำตอบทั่วไป:

- Password
- API key
- Token
- Private key
- PSK
- Credential
- ข้อมูลเฉพาะอุปกรณ์ของผู้ใช้
- IP, hostname หรือ topology ส่วนตัว เว้นแต่ผู้ใช้ให้มาเพื่อวิเคราะห์งานเฉพาะครั้ง

## Verification Request

เมื่อต้องทดสอบว่าเข้าถึง reference ได้ ให้รันคำขอนี้:

```text
เปิด Google Drive reference ตามลิงก์ที่ให้
อ่าน START_HERE.md → HERMES_AGENT_PROMPT.md → AGENT_USAGE.md → references/index.md
รายงานชื่อไฟล์ที่พบ และสรุปกฎความปลอดภัย 3 ข้อ
ห้ามเดาจากความจำ และห้ามสร้างคำสั่ง FortiOS ก่อนอ่าน reference
```

ผลลัพธ์ที่ถูกต้องต้องยืนยันว่า:

- เป็นคู่มือทั่วไป FortiOS 7.4.13 สำหรับหลายโมเดล
- ใช้การอ่าน topic เฉพาะเรื่องเพื่อลด context
- ต้องตรวจสอบ live configuration และ hardware-specific details ก่อนเปลี่ยนแปลงจริง

## If Access Fails

ให้ตอบเพียงว่า:

```text
ไม่สามารถเข้าถึง Google Drive FortiOS 7.4.13 reference ได้
ยังไม่ได้อ่านเนื้อหาคู่มือ จึงไม่ควรเดาคำสั่งหรือขั้นตอน configuration
```

ห้ามแต่งเนื้อหาของ reference ขึ้นเองเมื่อเปิดไฟล์ไม่ได้.
