# ODOOIMP — คู่มือการใช้งาน Jira Project

คู่มือการทำงานสำหรับ Jira Project **Odoo Implementation Phase** (คีย์โปรเจกต์ `ODOOIMP`, ไซต์ `pde-main-team.atlassian.net`) ซึ่งครอบคลุมการดำเนินโครงการ Odoo ERP ของ PEM/PEMC

คู่มือนี้ควบคุมเวอร์ชันผ่าน Repository นี้แทนการใช้ Confluence — ดูขั้นตอนการเปลี่ยนแปลงด้านล่าง

## สารบัญ

| เอกสาร | เนื้อหา |
|---|---|
| [ประเภท Issue](docs/issue-types-th.md) | Issue Type แต่ละประเภทใช้ทำอะไร เมื่อไหร่ควรใช้ และฟิลด์สำคัญของแต่ละประเภท |
| [ฟิลด์อ้างอิง](docs/field-reference-th.md) | ฟิลด์ Custom Field ทั้งหมด พร้อม Field ID ประเภทข้อมูล และค่าที่อนุญาต ดึงตรงจากการตั้งค่าจริงของโปรเจกต์ |
| [เวิร์กโฟลว์](docs/workflows-th.md) | สถานะและชื่อ Transition ของทุก Issue Type |
| [ตารางสปรินต์](docs/sprint-schedule-th.md) | ปฏิทินสปรินต์ทั้ง 29 สปรินต์ ตั้งแต่ 21 ก.ย. 2026 – 29 ต.ค. 2027 |

## ข้อมูลโดยสรุป

- **โปรเจกต์:** Odoo Implementation Phase (`ODOOIMP`)
- **บอร์ด:** EXAMPLE board (id `1441`)
- **Epic (แบ่งตามเฟส):** 01-Project Initiation → 09-Hypercare Support (ดูรายการทั้งหมดที่ [ประเภท Issue](docs/issue-types-th.md#โครงสร้าง-epic-ใน-odooimp))
- **Issue Type:** Epic, Story, Task, Subtask, Bug, Milestone (custom), Change Request (custom)

## วิธีใช้ Repository นี้

- **อ่าน:** เปิดไฟล์ `.md` ใดก็ได้ด้านบน — GitHub จะแสดงตารางและหัวข้อโดยอัตโนมัติ ไม่ต้องใช้เครื่องมือเพิ่มเติม
- **แก้ไข:** เปิด Pull Request แทนการ push ตรงเข้า `main` เพราะการเปลี่ยนเอกสารเวิร์กโฟลว์โดยไม่มีการตรวจสอบ คือสิ่งที่ Repository นี้ถูกสร้างขึ้นมาเพื่อป้องกัน
- **รักษาให้ตรงกับ Jira:** หากฟิลด์ สถานะ หรือ Transition มีการเปลี่ยนแปลงใน Jira Project Settings ให้อัปเดตเอกสารที่เกี่ยวข้องใน PR เดียวกัน — ถือว่าความไม่ตรงกันระหว่าง Repository นี้กับโปรเจกต์จริงเป็นข้อบกพร่อง (Bug)

## สิ่งที่ไม่ได้ครอบคลุมในคู่มือนี้

คู่มือนี้บันทึกเรื่อง *โครงสร้างของโปรเจกต์เป็นอย่างไร* — Issue Type, ฟิลด์, เวิร์กโฟลว์, สปรินต์ แต่ไม่ครอบคลุมแผนการดำเนินโครงการเอง (เฟส, กำหนดเวลา, ขอบเขตงานแยกตามโมดูล) ซึ่งอยู่ใน Blueprint และเอกสาร BPR ของโครงการ
