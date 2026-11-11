# 🏫 KMITL Classroom Booking System (v3)

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg?logo=python&logoColor=white)](https://www.python.org/)
[![Database](https://img.shields.io/badge/MySQL-8.0%2B-orange.svg?logo=mysql&logoColor=white)](https://www.mysql.com/)
[![GUI](https://img.shields.io/badge/GUI-Tkinter-green.svg)](https://docs.python.org/3/library/tkinter.html)
[![License](https://img.shields.io/badge/License-Academic-lightgrey.svg)]()

**KMITL Classroom Booking** คือ เดสก์ท็อปแอปพลิเคชัน (Desktop Application) สำหรับระบบบริหารจัดการและจองห้องเรียนออนไลน์ พัฒนาขึ้นด้วยภาษา **Python (Tkinter)** ร่วมกับฐานข้อมูล **MySQL** เหมาะสำหรับใช้งานในระดับสถาบันหรือคณะ เพื่ออำนวยความสะดวกแก่อาจารย์และนักศึกษาในการจัดสรรพื้นที่สำหรับการเรียน การสอนเสริม การติวสอบ หรือการทำงานกลุ่มได้อย่างเป็นระเบียบ

---

## 🌟 จุดเด่นและฟีเจอร์หลัก (Key Features)

- 🔐 **ระบบจัดการสมาชิกและเข้าสู่ระบบ (Authentication System):**
  - สมัครสมาชิกโดยแยกบทบาทเป็น **นักศึกษา 🎓** หรือ **อาจารย์ 📚**
  - รองรับการล็อกอินด้วย **ชื่อ-นามสกุล** หรือ **อีเมล**
  - เข้ารหัสรหัสผ่านด้วยอัลกอริทึม **PBKDF2-SHA256 + Salt แบบสุ่ม** (ไม่เก็บ Plaintext Password)
- 🗓️ **ตารางจองห้องแบบเรียลไทม์ (14-Day Advance Booking):**
  - ดูสถานะห้องว่าง/ถูกจองแล้วล่วงหน้าได้ 14 วัน
  - แสดงรายละเอียดอุปกรณ์ประจำห้อง (โปรเจกเตอร์, เครื่องปรับอากาศ, คอมพิวเตอร์, Wi-Fi ฯลฯ)
  - กำหนดความจุสูงสุดของแต่ละห้อง พร้อมระบบแจ้งเตือนหากกรอกจำนวนผู้ใช้เกินความจุ
- 📌 **ระบบการจองของฉัน (My Bookings):**
  - ดูรายการจองที่กำลังจะมาถึงของผู้ใช้งานปัจจุบันในหน้าเดียว
  - ป้องกันสิทธิ์การลบ: **ยกเลิกได้เฉพาะการจองของตนเองเท่านั้น**
- 📜 **ประวัติการทำรายการอัตโนมัติ (Automated Audit History Log):**
  - ตรวจสอบประวัติการจองและยกเลิกทั้งหมดย้อนหลังได้
  - ทำงานด้วย **MySQL Triggers** ในระดับฐานข้อมูล ทำให้ประวัติไม่สูญหายแม้รายการจองหลักถูกลบ
- 🎨 **Modern Native UI/UX:**
  - วาดองค์ประกอบภาพ กราเดียนต์ โลโก้ และไอคอนแอปพลิเคชันด้วย Python Canvas **โดยไม่ต้องพึ่งไฟล์รูปภาพภายนอก**

---

## 🛠️ เทคโนโลยีที่ใช้ (Tech Stack & Security Highlights)

| ส่วนประกอบ | เทคโนโลยี / อัลกอริทึม | รายละเอียด |
| :--- | :--- | :--- |
| **Front-end** | Python 3 + Tkinter | ออกแบบ Custom UI, Canvas Drawing, Flat Components |
| **Back-end & Logic** | Python Logic | Data Validation, Error Handling, Session Management |
| **Database** | MySQL 8.0+ | Engine: InnoDB, UTF-8 (utf8mb4_unicode_ci) |
| **Middleware** | `mysql-connector-python` | เชื่อมต่อฐานข้อมูลผ่าน Parameterized Queries (`%s`) |
| **Security** | PBKDF2-SHA256 | เข้ารหัสรหัสผ่านวน 200,000 รอบ + Salt สุ่ม 16 ไบต์ |
| **Timing Protection** | `hmac.compare_digest` | ป้องกันการโจมตีประเภท Timing Attack ขณะยืนยันรหัสผ่าน |

---

## 🏗️ สถาปัตยกรรมระบบ (System Architecture)

ระบบออกแบบตามหลัก **3-Tier Architecture** เพื่อแยกส่วนการแสดงผล ลอจิกการทำงาน และการจัดการข้อมูลอย่างชัดเจน:

```
[ Front-end (Tkinter GUI) ]
          │
          ▼  (Event / Input Data)
[ Middleware & Logic Layer (Python) ] ── (PBKDF2 Hash / Parameterized SQL) ──┐
          │                                                                 │
          ▼  (Read / Write Operations)                                     ▼
[ Back-end Database (MySQL) ] ─── (Triggers) ───► [ History Log Table ]
```

---

## ⚙️ ขั้นตอนการติดตั้งและการรันโปรแกรม (Getting Started)

### 1. ความต้องการของระบบ (Prerequisites)
- **Python 3.8+**
- **MySQL Server 8.0+** (หรือผ่าน XAMPP / MySQL Workbench)

### 2. การติดตั้งไลบรารี
เปิด Terminal / Command Prompt แล้วพิมพ์คำสั่ง:
```bash
pip install mysql-connector-python
```

### 3. การเตรียมฐานข้อมูล (Database Setup)
1. เปิดโปรแกรม **MySQL Workbench** แล้วเชื่อมต่อกับ MySQL Server ในเครื่องของคุณ
2. เปิดไฟล์สคริปต์ `classroom_booking_mysql.sql`
3. สั่ง Execute (กดไอคอนสายฟ้า ⚡) เพื่อสร้างฐานข้อมูลชื่อ `project` พร้อมตารางและ Triggers ทั้งหมด

### 4. การตั้งค่ารหัสผ่านฐานข้อมูล (Configuration)
เปิดไฟล์ `projectxworkbench.py` แล้วแก้ไขตัวแปร `MYSQL_CONFIG` ในโค้ด (ช่วงประมาณบรรทัดที่ 220) ให้ตรงกับรหัสผ่าน MySQL เครื่องของคุณ:

```python
MYSQL_CONFIG = {
    "host": "localhost",
    "port": 3306,
    "user": "root",
    "password": os.environ.get("DB_PASSWORD", "YOUR_MYSQL_PASSWORD"),  # ใส่รหัสผ่าน MySQL ของคุณที่นี่
    "database": "project",
    "charset": "utf8mb4",
}
```

### 5. สั่งรันแอปพลิเคชัน
```bash
python projectxworkbench.py
```

---

## 🗄️ โครงสร้างฐานข้อมูล (Database Schema)

- `users` : เก็บข้อมูลสมาชิก (user_id, role, first_name, last_name, email, password_hash)
- `rooms` : เก็บรายชื่อห้องเรียน ความจุ อาคาร และสีประจำห้อง
- `equipment` & `room_equipment` : เก็บข้อมูลอุปกรณ์และจำนวนอุปกรณ์ประจำแต่ละห้อง (Many-to-Many)
- `time_slots` : เก็บคาบเวลา (08:00 – 18:00 น.)
- `bookings` : เก็บข้อมูลการจองปัจจุบัน มี `UNIQUE KEY (room_id, booking_date, slot_id)` กันการจองซ้ำ
- `booking_details` : เก็บข้อมูลเพิ่มเติมของการจอง (รหัสประจำตัว, เบอร์โทร, จำนวนผู้เข้าใช้)
- `history` : เก็บประวัติการจองและยกเลิก (บันทึกอัตโนมัติผ่าน Database Triggers)

---

## 👥 ผู้จัดทำและบทบาทหน้าที่ (Development Team - Agile Model)

พัฒนาภายใต้แนวคิด **Agile Methodology** โดยแบ่งบทบาทการทำงานในทีมดังนี้:

| ชื่อ-นามสกุล | รหัสนักศึกษา | บทบาทในโปรเจกต์ (Agile Role) | Responsibilities |
| :--- | :---: | :---: | :--- |
| **นาย ณัฐพัฒน์ ศรีเตชะ** | `69030325` | **Product Owner** | วางแผนโครงงาน จัดลำดับความสำคัญของฟีเจอร์ และควบคุมขอบเขตระบบ |
| **นางสาว ภูริชญา โฉมศรี** | `69030195` | **Database Designer** | ออกแบบ ER-Diagram, Schema, เขียน SQL Script และจัดการ Triggers |
| **นาย ภัทรกร อินทรกำแหง** | `69040442` | **UI/UX Designer** | ออกแบบโครงร่าง UI, Theme, Layouts และสร้าง Custom Components |
| **นาย วชิรวิทย์ ขุนนุช** | `69030210` | **Software Tester & Core Developer** | ทดสอบระบบ (Testing), จัดการ Security/Auth และปรับปรุงคุณภาพโค้ด |

---

## 📄 ใบอนุญาต (License)

โครงงานนี้จัดทำขึ้นเพื่อการศึกษา รายวิชาการพัฒนาซอฟต์แวร์ สถาบันเทคโนโลยีพระจอมเกล้าเจ้าคุณทหารลาดกระบัง (KMITL) 
