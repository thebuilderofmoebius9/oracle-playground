---
layout: doc
title: Glossary คำศัพท์
---

# Glossary — คำศัพท์ Oracle

คำศัพท์พื้นฐานสำหรับผู้เริ่มต้น (Level 0)

---

## 🤖 Agent

**คืออะไร:** AI ที่มี **บทบาท (role)** และ **เป้าหมาย (goal)** ชัดเจน

**ตัวอย่าง:**
- **Gravity Oracle** — วางแผนงาน + สั่งการ
- **GB Oracle** — รันงานตามที่ Gravity สั่ง
- **Codex** — (deprecated) ตัว execute code

**สำคัญทำไม:** Agent แต่ละตัวมีความเชี่ยวชาญต่างกัน — เหมือนทีมคน

---

## 🔧 Tool-calling

**คืออะไร:** AI **เรียก code/API จริง** — ไม่ใช่แค่ตอบจากความรู้

**ตัวอย่าง:**
```
User: "ตรวจสอบ vessel MWS-001, MWS-002 ให้หน่อย"
Oracle: [เรียก API inspection system จริง]
        └─ ได้ข้อมูลจริงกลับมา → สรุปให้คุณ
```

**สำคัญทำไม:** ทำให้ AI ไม่ใช่แค่ chatbot — แต่เป็น **assistant ที่ทำงานจริง** ได้

---

## 📏 Context Window

**คืออะไร:** **"หน่วยความจำระยะสั้น"** ของ AI — จำประโยคได้สั้นๆ ไม่กี่หน้า

**แบบเปรียบ:**
- **Context Window** = สมองสั้น (RAM) — จำได้แค่ 5 นาทีที่แล้ว
- **Memory System** = สมองยาว (Storage) — จำข้ามวัน ข้ามเดือน

**สำคัญทำไม:** ถ้าไม่มี Memory System → AI จะลืมทุกอย่างตอน context window เต็ม

---

## 🧠 Memory

**คืออะไร:** **"หน่วยความจำระยะยาว"** — ทำให้ AI จำ **ข้ามเซสชัน**

**ระดับความจำ:**
1. **Identity** — ผมคือใคร (ชื่อ, role, preferences)
2. **Project** — ทำอะไรอยู่ (โปรเจกต์, dependencies, patterns)
3. **Session** — คุยอะไรตอนนี้ (turn ปัจจุบัน, context ใกล้ๆ)

**สำคัญทำไม:** ทำให้ AI ไม่ต้องถามซ้ำ — สอนครั้งเดียว จำตลอด

---

## 💬 Session

**คืออะไร:** **หนึ่งรอบการใช้งาน** — อาจเป็น:
- เปิด browser → ปิด browser
- หรือ refresh หน้าเว็บ (ถ้า persist ผ่าน localStorage)

**ตัวอย่าง:**
```
Session 1: สอนว่า "ผมชื่อมิ่งขวัศ" → จำใน localStorage
Session 2: Refresh หน้า → Oracle ยังจำชื่ออยู่ ✨
```

**สำคัญทำไม:** Session คือ **boundary** ระหว่าง AI ที่ลืม กับ AI ที่จำ

---

## 🔌 MCP (Model Context Protocol)

**คืออะไร:** มาตรฐานให้ AI **เชื่อมกับ external tools/systems** — ทำให้ AI เรียก API/database/code ได้

**ตัวอย่าง:**
```
AI → MCP → GitHub API (ดึง PR จริง)
AI → MCP → Database (query data จริง)
AI → MCP → File System (อ่านไฟล์จริง)
```

**สำคัญทำไม:**
- ทำให้ AI ไม่ต้อง hardcode tool
- เชื่อม tool ใหม่ได้เร็ว — แค่ install MCP server

> ℹ️ **อ้างอิง:** [MCP Specification](https://spec.modelcontextprotocol.io/)

---

## 🧩 Skill

**คืออะไร:** **Plugin/Extension** สำหรับ Oracle — เพิ่มความสามารถเฉพาะทาง

**ตัวอย่าง:**
- `/learn` — สอน Oracle เรียน codebase
- `/rrr` — สรุป session retrospective
- `/trace` — ตามรอยไฟล์/pattern

**สำคัญทำไม:** ทำให้ Oracle **customizable** — เพิ่ม feature ได้โดยไม่แก้ core

---

## 🎯 Fleet

**คืออะไร:** ทีม **หลาย Agent** ทำงานร่วมกัน — แต่ละตัวมี role ต่างกัน

**ตัวอย่าง:**
- **Atom** — วางแผน (Planner)
- **GB** — รันงาน (Executor)
- **Codex** — (deprecated) execute code

**สำคัญทำไม:** ทำให้งานใหญ่แยกเป็นเล็กๆ — คนละ role เชี่ยวชาญคนละอย่าง

---

## 📊 Summary

| คำศัพท์ | แปลง่ายๆ |
|----------|-----------|
| Agent | AI ที่มีบทบาทชัดเจน |
| Tool-calling | AI เรียก code/API จริง |
| Context Window | สมองสั้น — จำได้นิดหน่อย |
| Memory | สมองยาว — จำข้ามเซสชัน |
| Session | หนึ่งรอบใช้งาน |
| MCP | มาตรฐานเชื่อม AI กับ tool |
| Skill | Plugin เพิ่มความสามารถ |
| Fleet | ทีมหลาย AI ทำงานร่วมกัน |

---

> 💡 **Tip:** ถ้าคำศัพท์อื่นงง — ไปถามได้ใน Discord หรือเปิด [Oracle 101](/oracle-playground/oracle101/) อ่านเพิ่ม
