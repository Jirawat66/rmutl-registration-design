# 06 — Requirement Mapping (Traceability Matrix)

ใช้ตรวจว่าทุก requirement มี Use Case, User Story, หน้าจอ และการทดสอบครบ ตอนพัฒนาให้เพิ่มคอลัมน์ **Issue / PR** เพื่อติดตามงาน

| FR | Use Case | User Story | Screen | Test Task | Priority | Actor ที่เกี่ยวข้อง | Issue / PR |
|---|---|---|---|---|---|---|---|
| FR-01 บันทึกและแก้ไขประวัติ | UC-01 | US-01 | SCR-01 | T-01 | Medium | นักศึกษา, เจ้าหน้าที่ทะเบียน | |
| FR-02 ตารางเรียน ตารางสอบ | UC-02 | US-02 | SCR-02 | T-02 | Normal | นักศึกษา | |
| FR-03 ปฏิทินการศึกษา | UC-03 | US-03 | SCR-03 | T-03 | Normal | นักศึกษา | |
| FR-04 ค้นหารายวิชาที่เปิดสอน | UC-04 | US-04 | SCR-04 | T-04 | Normal | นักศึกษา | |
| FR-05 ลงทะเบียนเรียน | UC-05 | US-05 | SCR-05 | T-05 | **Highest** | นักศึกษา | |
| FR-06 ถอนรายวิชา | UC-06 | US-06 | SCR-06 | T-06 | **Highest** | นักศึกษา, อาจารย์ที่ปรึกษา, เจ้าหน้าที่ทะเบียน | |
| FR-07 แสดงผลการลงทะเบียน | UC-07 | US-07 | SCR-07 | T-07 | Normal | นักศึกษา | |
| FR-08 แสดงผลการเรียน | UC-08 | US-08 | SCR-08 | T-08 | Normal | นักศึกษา | |
| FR-09 ยื่นขอสำเร็จการศึกษา | UC-09 | US-09 | SCR-09 | T-09 | Medium | นักศึกษา, อาจารย์/เจ้าหน้าที่ทะเบียน | |
| FR-10 สถานะการชำระเงินและหนี้สิน | UC-10 | US-10 | SCR-10 | T-10 | High | นักศึกษา | |

## Non-Functional Requirements

| NFR | ครอบคลุม | ตรวจที่ |
|---|---|---|
| NFR-01 Usability (≤ 3 taps) | ทุกหน้าจอ | Home → Hamburger menu → ฟังก์ชัน = 2 taps |
| NFR-02 Consistency | ทุก Component | `design/tokens/*`, [07-design-system.md](07-design-system.md) |
| NFR-03 Mobility (iOS + Android) | ทุกหน้าจอ | ทดสอบบนอุปกรณ์จริงทั้ง 2 ระบบ |

## Pain point → Requirement

| Pain point (Journey Map) | แก้ด้วย |
|---|---|
| เมนูซับซ้อน หาข้อมูลยาก | Home Dashboard + Hamburger menu (FR-02, FR-03, NFR-01) |
| ไม่แน่ใจว่าแก้ข้อมูลเองได้ไหม | ฟอร์มแยกข้อมูลทั่วไป / ข้อมูลอ่อนไหว (FR-01) |
| วิชาเต็ม ตารางซ้อน | แสดงที่นั่ง + เตือนตารางซ้อนก่อนยืนยัน (FR-04, FR-05) |
| ไม่รู้สถานะคำร้อง | Status Stepper (FR-06, FR-09) |
| ไม่รู้ยอดค้างชำระ / ช่องทางชำระ | หน้าสถานะ + ใบแจ้งชำระพร้อม QR (FR-10) |
| ไม่รู้ว่าเงื่อนไขจบครบไหม | Eligibility check + progress รายหมวด (FR-09) |
