---
layout: doc
title: โครงสร้างความจำ
---

# โครงสร้างความจำ Oracle — Memory Hierarchy

Oracle จำข้อมูลเป็น **ชั้นๆ** — ไม่ใช่โยนมั่วๆ ทั้งหมดไปในที่เดียว

---

## 🗺️ แผนที่ความจำ (Memory Map)

```
                    ┌─────────────────┐
                    │   IDENTITY      │
                    │  (ใครคือฉัน?)   │
                    └────────┬────────┘
                             │
                    ┌────────▼────────┐
                    │    PROJECT      │
                    │  (ทำอะไรอยู่)   │
                    └────────┬────────┘
                             │
                    ┌────────▼────────┐
                    │    SESSION      │
                    │ (คุยอะไรตอนนี้)│
                    └─────────────────┘
```

---

## 📁 1. Identity Layer — ระดับตัวตน

**เก็บอะไร:** ข้อมูลเกี่ยวกับ **คุณคือใคร**

| Field | ตัวอย่าง | อยู่ไหนใน ψ/ |
|-------|-----------|----------------|
| ชื่อ | มิ่งขวัศ | `ψ/memory/identity/` |
| Role | Country Manager | `ψ/memory/identity/` |
| Preferences | Vim ไม่ชอบ Nano | `ψ/memory/identity/` |
| Pronouns | เขา | `ψ/memory/identity/` |

**ลักษณะ:**
- แทบไม่เปลี่ยน — ใช้ทุก session
- เป็นพื้นฐานสำหรับ Oracle รู้จักคุณ

---

## 📂 2. Project Layer — ระดับโปรเจกต์

**เก็บอะไร:** ข้อมูลเกี่ยวกับ **โปรเจกต์/งานที่ทำ**

| Field | ตัวอย่าง | อยู่ไหนใน ψ/ |
|-------|-----------|----------------|
| ชื่อโปรเจกต์ | chevron-rig-move | `ψ/memory/projects/chevron-rig-move/` |
| Dependencies | React, TypeScript | `ψ/memory/projects/chevron-rig-move/` |
| Patterns | เคยใช้ Redux ไม่ใช่ Zustand | `ψ/memory/projects/chevron-rig-move/` |
| Context | ย้าย rig วันที่ 15 ม.ค. | `ψ/memory/projects/chevron-rig-move/` |

**ลักษณะ:**
- เปลี่ยนบ้าง — ขึ้นกับโปรเจกต์ที่ active
- ใช้เวลาทำงานโปรเจกต์นั้น

---

## 💬 3. Session Layer — ระดับเซสชัน

**เก็บอะไร:** ข้อมูล **turn ปัจจุบัน/ใกล้ๆ**

| Field | ตัวอย่าง | อยู่ไหนใน ψ/ |
|-------|-----------|----------------|
| ข้อความล่าสุด | "จำผมได้ไหม?" | `ψ/inbox/` หรือ context window |
| Context รอบๆ | กำลังคุยเรื่อง rig move | context window |
| Interactions count | 5 รอบแล้ว | `ψ/memory/session/` |

**ลักษณะ:**
- เปลี่ยนบ่อย — ทุก turn/click
- ใช้เฉพาะ session นี้

---

## 🗂️ โครงสร้าง ψ/ บนดิสก์จริง

```
ψ/                              # Root brain directory
├── memory/                      # เก็บข้อมูลระยะยาว
│   ├── identity/               # Identity layer
│   │   ├── name.md
│   │   ├── role.md
│   │   └── preferences.md
│   ├── projects/               # Project layer
│   │   ├── chevron-rig-move/
│   │   │   ├── context.md
│   │   │   ├── dependencies.md
│   │   │   └── patterns.md
│   │   └── fpso-replacement/
│   └── sessions/               # Session layer (ประวัติ session)
├── inbox/                      # ข้อความเข้า
├── writing/                    # งานเขียน
└── archive/                    # เก็บ archive
```

---

## 🔄 วงจรความจำ (Memory Lifecycle)

```
┌─────────────┐
│  New Turn   │  ← คุยกับ Oracle
└──────┬──────┘
       │
       ▼
┌─────────────┐
│ Extract     │  ← ดึงข้อมูลที่ควรจำ (name, project, preference)
└──────┬──────┘
       │
       ▼
┌─────────────┐
│ Categorize  │  ← Identity? Project? Session?
└──────┬──────┘
       │
       ▼
┌─────────────┐
│ Store       │  ← เก็บไว้ใน ψ/memory/ ตามชั้นที่ถูก
└──────┬──────┘
       │
       ▼
┌─────────────┐
│ Retrieve    │  ← session หน้า → ดึงกลับมาใช้
└─────────────┘
```

---

## 🎯 ทำไมต้องแบ่งชั้น?

| ถ้าแบ่งชั้น | ถ้าไม่แบ่งชั้น |
|-------------|----------------|
| ✅ หาได้เร็ว — รู้ว่าอยู่ไหน | ❌ สับสน — ข้อมูลปนกันหมด |
| ✅ Update ได้แม่น — แก้ project ไม่กระทบ identity | ❌ เสี่ยง — แก้ไปตัวนึงอาจทำทั้งหมดพัง |
| ✅ Prune ได้ — ลบ session เก่าได้โดยไม่หาย identity | ❌ ลบยาก — ลบอะไรไปอาจหายทั้งหมด |

---

## 💡 ตัวอย่างสด

```
คุณ: "ผมชื่อมิ่งขวัศ Country Manager สาย marine"
Oracle: ✅ เก็บใน Identity Layer

คุณ: "ดูแลโปรเจกต์ Chevron rig move"
Oracle: ✅ เก็บใน Project Layer

คุณ: "เอาวันนี้คุยอะไรไปบ้าง"
Oracle: ✅ ดึงจาก Session Layer + Project + Identity มาสรุป
```

---

## 📚 แนวคิดโครงสร้างความจำแบบชั้นๆ

แนวคิดนี้อ้างอิงจาก **ARRA/Muninn memory architecture** — ระบบความจำที่ออกแบบมาเพื่อให้ Oracle จำได้ลึกและเป็นระบบ

> ℹ️ **อ้างอิง:** [ARRA/Muninn Memory Architecture](https://github.com/Soul-Brews-Studio/arra-oracle-v3)
