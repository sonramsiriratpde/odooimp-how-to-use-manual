# ฟิลด์อ้างอิง (Field Reference)

ฟิลด์ Custom Field ทั้งหมดที่ตั้งค่าไว้ใน ODOOIMP ดึงข้อมูลโดยตรงจาก Field Metadata ของโปรเจกต์จริง Field ID (`customfield_XXXXX`) เป็นค่าเฉพาะของไซต์ Jira นี้เท่านั้น — อย่าสันนิษฐานว่าตรงกับโปรเจกต์อื่น เวอร์ชันภาษาอังกฤษอยู่ที่ [field-reference.md](field-reference.md)

## ฟิลด์ของ Epic

| ชื่อฟิลด์ | Field ID | ประเภท | จำเป็นต้องกรอก | ค่าที่อนุญาต |
|---|---|---|---|---|
| Owner | `customfield_11931` | User (เดี่ยว) | ไม่ | — |
| Entity | `customfield_11932` | Select (เดี่ยว) | ไม่ | `PEM`, `PEMC`, `Both` |
| Fix versions | `fixVersions` (built-in) | Version (หลายค่า) | ไม่ | `Go-Live Phases 1-1`, `Go-Live Phases 1-2` |

> หมายเหตุ: ปัจจุบันมี Fix Version เพียง 2 รายการเท่านั้น การวางแผนก่อนหน้านี้เคยพูดถึงชื่อ Release เช่น R3–R8 ที่แมปกับการสร้างระบบแต่ละโมดูล — แต่ยังไม่ได้ถูกสร้างเป็น Version จริงใน Jira

## ฟิลด์ของ Story

| ชื่อฟิลด์ | Field ID | ประเภท | จำเป็นต้องกรอก | ค่าที่อนุญาต |
|---|---|---|---|---|
| Solution Type | `customfield_11933` | Select (เดี่ยว) | ไม่ | `Standard`, `Configuration`, `Custom Development`, `Integration`, `Report/Form` |
| Acceptance Criteria | `customfield_11934` | Text (ย่อหน้า) | ไม่ | — |
| Functional Specification Document (FSD) link | `customfield_11935` | Text | ไม่ | — |
| Component | `customfield_11943` | Select (เดี่ยว) | ไม่ | ดู [ค่า Component](#ค่า-component-ใช้ร่วมกัน) |
| Story point estimate | `customfield_10016` | Number | ไม่ | — |

> หมายเหตุ: ฟิลด์ "BPR Ref ID" และฟิลด์ "Priority (MoSCoW)" แยกต่างหาก เคยถูกพูดถึงในขั้นตอนวางแผน แต่ **ไม่ได้** ถูกตั้งค่าเป็น Custom Field จริง มีเพียงฟิลด์ `Priority` แบบ built-in เท่านั้น (ดูด้านล่าง) ซึ่งมีชุดค่าที่ผสมกันอย่างไม่ปกติ

## ฟิลด์ของ Task

| ชื่อฟิลด์ | Field ID | ประเภท | จำเป็นต้องกรอก | ค่าที่อนุญาต |
|---|---|---|---|---|
| Component | `customfield_11943` | Select (เดี่ยว) | ไม่ | ดู [ค่า Component](#ค่า-component-ใช้ร่วมกัน) |
| Due date | `duedate` (built-in) | Date | **ใช่** | — |

## ฟิลด์ของ Bug

| ชื่อฟิลด์ | Field ID | ประเภท | จำเป็นต้องกรอก | ค่าที่อนุญาต |
|---|---|---|---|---|
| Environment | `customfield_11825` | Select (เดี่ยว) | **ใช่** | `Development (DEV)`, `System Integrate Test (SIT)`, `Production (PROD)` |
| Serverity *(ชื่อฟิลด์ตามที่ตั้งค่าไว้จริง — สะกดผิด)* | `customfield_11936` | Select (เดี่ยว) | **ใช่** | `Low`, `Medium`, `High`, `Critical` |
| Steps to Reproduce | `customfield_11937` | Text (ย่อหน้า) | **ใช่** | — |
| Component | `customfield_11943` | Select (เดี่ยว) | ไม่ | ดู [ค่า Component](#ค่า-component-ใช้ร่วมกัน) |

## ฟิลด์ของ Milestone

| ชื่อฟิลด์ | Field ID | ประเภท | จำเป็นต้องกรอก | ค่าที่อนุญาต |
|---|---|---|---|---|
| Sign-off Owner | `customfield_11938` | User (หลายค่า) | **ใช่** | — |
| Linked Deliverables | `customfield_11939` | Text แต่ **ตรวจสอบเป็น URL** | ไม่ | ต้องเป็น URL ที่ถูกต้อง — ข้อความอิสระหรือ Issue Key จะถูกปฏิเสธ |

## ฟิลด์ของ Change Request

| ชื่อฟิลด์ | Field ID | ประเภท | จำเป็นต้องกรอก | ค่าที่อนุญาต |
|---|---|---|---|---|
| Impact | `customfield_11940` | Select (หลายค่า) | **ใช่** | `Time`, `Cost`, `Scope` |
| Requested By | `customfield_11941` | User (หลายค่า) | **ใช่** | — |
| Approvals | `customfield_10032` | Jira Service Management `sd-approvals` | ไม่ | ไม่สามารถตั้งค่าได้ตอนสร้าง Issue ใช้สำหรับ Workflow การอนุมัติของ JSM ไม่ใช่ตัวเลือก Approver แบบง่าย |

## ค่า Component (ใช้ร่วมกัน)

ฟิลด์ `Component` (`customfield_11943`) ใช้ร่วมกันระหว่าง Story, Task และ Bug ปัจจุบันมีค่าที่ละเอียดกว่ารายการโมดูลทั่วไป:

`Purchase` · `Sales` · `Inventory` · `Accounting` · `Finance` · `Manufacturing` · `Project Management` · `Quality Control` · `Maintenance` · `Repair` · `Fleet / Logistic` · `Product Lifecycle Management (PLM)` · `Helpdesk` · `Payroll`

## ฟิลด์ Priority (built-in)

Story (และ Issue Type อื่นที่ใช้ฟิลด์ `priority` แบบ built-in) ปัจจุบันมีชุดค่าที่ผสมกัน — ทั้งชุดค่าเริ่มต้นของ Jira และชุดค่าที่ปรับแต่งเองปรากฏอยู่ด้วยกัน:

`normal`, `urgent`, `Highest`, `High`, `Medium`, `Low`, `Lowest`

ลักษณะนี้เหมือนมี Priority Scheme ซ้อนกันอยู่ 2 ชุด มากกว่าจะเป็นชุดค่าที่สะอาดชุดเดียว ควรพิจารณาทำความสะอาดใน Jira Admin หากสร้างความสับสนตอนสร้าง Issue
