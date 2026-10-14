# RMUTL Registration System — UX/UI Design Handoff

เอกสารส่งต่องานออกแบบ (Design Handoff) ของ **แอปพลิเคชันระบบทะเบียนนักศึกษา มหาวิทยาลัยเทคโนโลยีราชมงคลล้านนา (RMUTL)** สำหรับ Developer ที่จะนำไปพัฒนาเป็นแอปจริง

> **สถานะ:** High-Fidelity Interactive Prototype (Figma) ผ่านการทดสอบกับผู้ใช้แล้ว ได้คะแนน SUS 92.5 และอัตราทำภารกิจสำเร็จ 100%
> ยังไม่มี Backend / API / Database เพราะขอบเขตงานคือการออกแบบ UX/UI เท่านั้น

---

## ลิงก์สำคัญ

| รายการ | ลิงก์ |
|---|---|
| Figma — Design System & Screens | [RMUTL mobile app](https://www.figma.com/design/B7ZQ63hxqiySFujkzQBvpm/RMUTL-mobile-app?node-id=11-2) |
| Interactive Prototype (กดทดลองได้) | https://rmutl.link/XuYo9 |
| Figma Full Frame Overview | https://rmutl.link/iCAXuKmy |
| เอกสารออกแบบฉบับเต็ม (PDF) | [`reference/design-spec.pdf`](reference/design-spec.pdf) |

แนะนำให้เปิด Figma ด้วย **Dev Mode** เพื่อดูขนาด ระยะห่าง และ export asset ของแต่ละหน้าจอ

---

## เริ่มอ่านจากตรงไหน

| # | เอกสาร | เนื้อหา | ใช้ทำอะไร |
|---|---|---|---|
| 1 | [Overview](docs/01-overview.md) | ขอบเขต, ผู้ใช้, Tech assumptions | ทำความเข้าใจภาพรวม |
| 2 | [User Research](docs/02-user-research.md) | Persona, Empathy Map, Journey Map | เข้าใจ Pain point ของผู้ใช้ |
| 3 | [SRS](docs/03-srs.md) | FR, NFR, User Story, Acceptance Criteria, Priority | **วางแผน Sprint / เปิด Issue** |
| 4 | [Use Cases](docs/04-use-cases.md) | UC-01 ถึง UC-10 พร้อม Activity และ Sequence Diagram | **เขียน Logic และเงื่อนไข** |
| 5 | [Screens](docs/05-screens.md) | หน้าจอทั้งหมด, Navigation, Sitemap | **สร้าง UI / Routing** |
| 6 | [Requirement Mapping](docs/06-requirement-mapping.md) | FR ↔ UC ↔ US ↔ Screen | ตรวจว่าทำครบ |
| 7 | [Design System](docs/07-design-system.md) | สี, ตัวอักษร, Component, State | **สร้าง Theme / Component library** |
| 8 | [Usability Testing](docs/08-usability-testing.md) | ผลทดสอบ Task-based, SUS | รู้ว่าจุดไหนผู้ใช้ติดขัด |
| 9 | [Dev Backlog & Open Questions](docs/09-backlog.md) | สิ่งที่ต้องทำต่อ / ต้องตัดสินใจ | **เริ่มพัฒนา** |

---

## โครงสร้าง Repository

```
.
├── README.md
├── docs/                        # เอกสารข้อกำหนดและการออกแบบ (Markdown)
│   ├── 01-overview.md … 09-backlog.md
│   └── images/
│       ├── diagrams/            # Use Case, Activity, Sequence, Sitemap
│       └── research/            # Persona, Journey Map, Framework
├── design/
│   ├── tokens/
│   │   ├── tokens.json          # Design Tokens (W3C DTCG) สร้างจาก Figma Styles
│   │   └── tokens.css           # CSS Variables พร้อมใช้
│   ├── figma/                   # ไฟล์ export ดิบจาก Figma (Styles + Prototype Variables)
│   ├── screens/                 # ภาพหน้าจอ Hi-Fi (ตั้งชื่อตามรหัส SCR)
│   ├── wireframes/              # Wireframe Grayscale
│   ├── flows/                   # ลำดับหน้าจอของ Happy Path ที่ทดสอบแล้ว
│   └── system/                  # Color Tokens, Component States, Typography, Mood Board
└── reference/
    └── design-spec.pdf          # เอกสารฉบับเต็ม (ตัดข้อมูลส่วนบุคคลออกแล้ว)
```

---

## สรุปฟีเจอร์ (10 ฟังก์ชันหลัก)

| ID | ฟังก์ชัน | Priority | Screen |
|---|---|---|---|
| FR-01 | บันทึกและแก้ไขประวัติส่วนตัว | Medium | SCR-01 |
| FR-02 | ตารางเรียน / ตารางสอบ | Normal | SCR-02 |
| FR-03 | ปฏิทินการศึกษา | Normal | SCR-03 |
| FR-04 | ค้นหารายวิชาที่เปิดสอน | Normal | SCR-04 |
| FR-05 | ลงทะเบียนเรียน | **Highest** | SCR-05 |
| FR-06 | ถอนรายวิชา (อนุมัติ 2 ระดับ) | **Highest** | SCR-06 |
| FR-07 | แสดงผลการลงทะเบียน | Normal | SCR-07 |
| FR-08 | แสดงผลการเรียน (GPA/GPAX) | Normal | SCR-08 |
| FR-09 | ยื่นขอสำเร็จการศึกษา | Medium | SCR-09 |
| FR-10 | สถานะการชำระเงินและหนี้สิน | High | SCR-10 |

หน้าจอเสริม: Login, Forgot Password, Home (Dashboard)

---

## ใช้ Design Tokens

```css
@import "design/tokens/tokens.css";

.button-primary {
  background: var(--color-button-default);
  border-radius: var(--radius-button);
  font: var(--text-button);
  padding: var(--space-1) var(--space-2);
}
```

ถ้าใช้ Flutter / React Native / Tailwind ให้แปลงจาก `tokens.json` (เช่นใช้ [Style Dictionary](https://amzn.github.io/style-dictionary/)) เพื่อให้ค่าตรงกับ Figma ตลอด

---

## ลิขสิทธิ์

ผลงานนี้เป็นส่วนหนึ่งของปริญญานิพนธ์ หลักสูตรวิศวกรรมศาสตรบัณฑิต สาขาวิศวกรรมคอมพิวเตอร์ มหาวิทยาลัยเทคโนโลยีราชมงคลล้านนา (ปีการศึกษา 2569)
ลิขสิทธิ์เป็นของคณะวิศวกรรมศาสตร์ มหาวิทยาลัยเทคโนโลยีราชมงคลล้านนา

> ข้อมูลในภาพหน้าจอ (ชื่อ รหัสนักศึกษา อีเมล รูปถ่าย ชื่ออาจารย์) เปลี่ยนเป็นข้อมูลตัวอย่างแล้ว
