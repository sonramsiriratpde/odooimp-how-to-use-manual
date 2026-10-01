# ประเภท Issue (Issue Types)

ODOOIMP ตั้งค่า Issue Type ไว้ทั้งหมด 7 ประเภท หน้านี้ให้นิยามของแต่ละประเภท เมื่อไหร่ควรใช้ และฟิลด์สำคัญ — ชื่อ Issue Type และชื่อฟิลด์คงไว้เป็นภาษาอังกฤษเนื่องจากเป็นค่าที่ตั้งไว้จริงในระบบ Jira ดู Field ID และค่าที่อนุญาตแบบละเอียดได้ที่ [ฟิลด์อ้างอิง](field-reference-th.md) และสถานะ/Transition ได้ที่ [เวิร์กโฟลว์](workflows-th.md) เวอร์ชันภาษาอังกฤษอยู่ที่ [issue-types.md](issue-types.md)

## Epic

**นิยาม:** งานก้อนใหญ่ที่รวบรวม Story, Task และ Issue อื่น ๆ ที่เกี่ยวข้องกันไว้ภายใต้ผลลัพธ์เดียว
**คำอธิบาย:** ไม่มีเกณฑ์การยอมรับ (Acceptance Criteria) เป็นของตัวเอง — เป็นเพียง "ภาชนะ" ที่ติดตามผ่าน Fix Version, Owner และ Entity จะปิดได้ก็ต่อเมื่องานทั้งหมดภายในเสร็จสิ้นแล้วเท่านั้น

| ฟิลด์ | วัตถุประสงค์ |
|---|---|
| Owner | ผู้รับผิดชอบหลักของ Epic นี้ — โดยทั่วไปคือหัวหน้าโมดูลหรือหัวหน้า Workstream |
| Entity | ขอบเขตงานนี้ใช้กับ `PEM`, `PEMC` หรือ `Both` |
| Fix versions | Epic นี้จะถูกส่งมอบใน Release ใด |

### โครงสร้าง Epic ใน ODOOIMP

โปรเจกต์นี้จัดโครงสร้างตามเฟสการดำเนินงาน ไม่ใช่ตามโมดูล:

| Key | Epic |
|---|---|
| ODOOIMP-1 | 01-Project Initiation |
| ODOOIMP-9 | 02-Assessment & Gap Analysis |
| ODOOIMP-10 | 03-Blueprint & Solution Design |
| ODOOIMP-11 | 04-System Build |
| ODOOIMP-12 | 05-Data Migration |
| ODOOIMP-13 | 06-Testing |
| ODOOIMP-14 | 07-User Enablement (Training) |
| ODOOIMP-15 | 08-Deployment |
| ODOOIMP-95 | 09-Hypercare Support |

งานสร้างระบบระดับโมดูล (Sales, Purchase, Inventory, Manufacturing ฯลฯ) จะอยู่ในรูปแบบ Story ภายใต้ **04-System Build** โดยแยกความแตกต่างด้วยฟิลด์ Component แทนที่จะแยกเป็น Epic ต่างหาก

## Story

**นิยาม:** หน่วยของฟังก์ชันทางธุรกิจที่ผู้ใช้มองเห็นได้ พร้อมเกณฑ์การยอมรับที่ชัดเจน
**คำอธิบาย:** ครอบคลุมทั้งงาน Configuration มาตรฐาน, การพัฒนาแบบ Custom, การเชื่อมต่อระบบ (Integration) และรายงาน โดยฟิลด์ Solution Type เป็นตัวแยกความแตกต่างเหล่านี้ ไม่ใช่ Issue Type — นี่คือสิ่งที่ SIT และ UAT ใช้ทดสอบเทียบ

| ฟิลด์ | วัตถุประสงค์ |
|---|---|
| Component | Story นี้อยู่ในโมดูล Odoo ใด |
| Solution Type | Standard / Configuration / Custom Development / Integration / Report-Form |
| Acceptance Criteria | เงื่อนไขที่ทดสอบได้ ซึ่ง SIT และ UAT ใช้ตรวจสอบ |
| Functional Specification Document (FSD) link | ลิงก์ไปยัง FSD หากมี |

**ตัวอย่าง:** [ODOOIMP-103](https://pde-main-team.atlassian.net/browse/ODOOIMP-103) — "As a Purchasing Officer, I want PR-to-PO approval routed by amount..."

## Task

**นิยาม:** กิจกรรมของโครงการที่จำเป็นต่อการดำเนินโครงการ แต่ไม่มีเกณฑ์การยอมรับทางธุรกิจเป็นของตัวเอง
**คำอธิบาย:** ครอบคลุมงานอย่างการฝึกอบรม, การเตรียมข้อมูล, การรัน Test หรือขั้นตอน Cutover — ขับเคลื่อนด้วยกำหนดเวลามากกว่าการให้คะแนน Story Point และมักมีผู้รับผิดชอบเพียงคนเดียว

| ฟิลด์ | วัตถุประสงค์ |
|---|---|
| Component | กิจกรรมนี้เกี่ยวข้องกับโมดูลหรือ Workstream ใด |
| Due date | **จำเป็นต้องกรอก** Task ขับเคลื่อนด้วยกำหนดเวลา ไม่ใช้ Story Point |

> Task ในโปรเจกต์นี้ไม่มีฟิลด์ Checklist ในตัว ให้ใส่ Checklist ไว้ในฟิลด์ Description แทน หรือแตกเป็น Subtask หากต้องการติดตามสถานะแยกแต่ละขั้นตอน

**ตัวอย่าง:** [ODOOIMP-108](https://pde-main-team.atlassian.net/browse/ODOOIMP-108) — "Execute SIT — PR-to-PO Approval Workflow (Purchase)"

## Subtask

**นิยาม:** ขั้นตอนย่อยในการดำเนินงานที่จำเป็นเพื่อให้ Story หรือ Task หลักเสร็จสมบูรณ์
**คำอธิบาย:** ต้องมี Parent เสมอ — นี่คือระดับที่ผู้ปฏิบัติงานแต่ละคนมักได้รับมอบหมาย

**ตัวอย่าง:** [ODOOIMP-104](https://pde-main-team.atlassian.net/browse/ODOOIMP-104) — "Configure multi-level approval workflow in Purchase module" ซึ่งเป็น Subtask ของ ODOOIMP-103

## Bug

**นิยาม:** ข้อบกพร่อง (Defect) ที่พบระหว่าง SIT, UAT หรือช่วง Hypercare/การสนับสนุนหลัง Production ซึ่งเบี่ยงเบนไปจากพฤติกรรมที่คาดหวัง
**คำอธิบาย:** ติดตามตั้งแต่พบปัญหาไปจนถึงแก้ไข ทดสอบซ้ำ และยืนยันผล

| ฟิลด์ | วัตถุประสงค์ |
|---|---|
| Environment | **จำเป็นต้องกรอก** พบปัญหาที่ไหน — DEV, SIT หรือ PROD |
| Serverity *(สะกดตามที่ตั้งค่าไว้จริง)* | **จำเป็นต้องกรอก** Low / Medium / High / Critical — ชื่อฟิลด์นี้สะกดผิดมาตั้งแต่ตั้งค่า ดู [ฟิลด์อ้างอิง](field-reference-th.md) |
| Steps to Reproduce | **จำเป็นต้องกรอก** ขั้นตอนการทำซ้ำปัญหาแบบชัดเจน |
| Component | ข้อบกพร่องนี้อยู่ในโมดูลใด |

**ตัวอย่าง:** [ODOOIMP-105](https://pde-main-team.atlassian.net/browse/ODOOIMP-105) — "PO approval bypassed when PR amount is edited after initial submission"

## Milestone *(custom)*

**นิยาม:** จุดสำคัญของการ Sign-off หรือวันที่สำคัญบน Timeline ของโครงการ ไม่ใช่หน่วยงานในตัวเอง
**คำอธิบาย:** ติดตาม Sign-off Owner และ Linked Deliverables ที่ต้องเสร็จสิ้นก่อนจะทำเครื่องหมายเป็น Achieved ได้

| ฟิลด์ | วัตถุประสงค์ |
|---|---|
| Sign-off Owner | **จำเป็นต้องกรอก** ผู้มีอำนาจ Sign-off ที่ระบุชื่อไว้ |
| Linked Deliverables | URL ที่ชี้ไปยัง Issue ที่ Milestone นี้ขึ้นอยู่กับ (ต้องเป็น URL ที่ถูกต้อง ไม่ใช่ข้อความอิสระ) |

**ตัวอย่าง:** [ODOOIMP-106](https://pde-main-team.atlassian.net/browse/ODOOIMP-106) — "Sprint-3 UAT Sign-Off — Sales, Purchase, Inventory"

## Change Request *(custom)*

**นิยาม:** คำขอเปลี่ยนแปลงขอบเขตงาน, กำหนดเวลา หรือต้นทุนที่ได้รับอนุมัติแล้ว ซึ่งยื่นขอหลังจากการ Sign-off Blueprint
**คำอธิบาย:** ต้องมีการประเมินผลกระทบและได้รับอนุมัติจากผู้สนับสนุนโครงการก่อนจึงจะดำเนินการได้ — แตกต่างจาก Bug (ข้อบกพร่องที่ไม่ได้ตั้งใจ) และ Story (ขอบเขตงานที่วางแผนไว้ตั้งแต่แรก)

| ฟิลด์ | วัตถุประสงค์ |
|---|---|
| Impact | **จำเป็นต้องกรอก** หนึ่งค่าหรือมากกว่า จาก Time / Cost / Scope |
| Requested By | **จำเป็นต้องกรอก** ผู้ยื่นคำขอเปลี่ยนแปลง |
| Approvals | ฟิลด์ Approvals ของ Jira Service Management — ไม่สามารถตั้งค่าได้โดยตรงตอนสร้าง Issue และไม่มีฟิลด์ "Approver" แยกต่างหาก |

**ตัวอย่าง:** [ODOOIMP-107](https://pde-main-team.atlassian.net/browse/ODOOIMP-107) — "Add credit-limit hold on Sales Order confirmation"
