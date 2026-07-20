---
layout: doc
title: ตัวอย่าง
---

# ตัวอย่างการใช้งานจริง

## 🌊 สำหรับคนทำงาน Offshore & Marine

### Example 1: จำ context โครงการข้ามวัน

**สถานการณ์:** คุณเป็น Country Manager ดูแลโครงการ Chevron rig move วันนี้คุย Oracle เยอะๆ แล้วกลับบ้าน พรุ่งนี้มาเปิดใหม่ — Oracle จำวันนี้คุยอะไรไปบ้างหมด

```
วันนี้ (ครั้งแรก):
└─ User: "ผมดูแลโปรเจกต์ Chevron rig move ครับ"
   Oracle: ✅ จำแล้วครับ Country Manager สาย marine

วันนี้ (ตอนจบ):
└─ User: "สรุปวันนี้คุยอะไรไปบ้าง"
   Oracle: 📋 คุยเรื่อง rig move timeline, schedule ย้ายที่ 15 ม.ค., ค่าใช้จ่าย...

พรุ่งนี้ (เปิด session ใหม่):
└─ User: "เมื่อวานคุยอะไรไปบ้าง?"
   Oracle: 📋 วานคุยเรื่อง rig move... [ทุกอย่างอยู่หมด] ✨
```

**จุดเด่น:** ไม่ต้องอธิบายซ้ำว่าคุณคือใคร ทำโปรเจกต์อะไร — Oracle จำไว้ให้

---

### Example 2: Tool-calling ดึงข้อมูลระบบ Vessel Inspection

**สถานการณ์:** คุณต้องตรวจสอบข้อมูล vessel หลายลำจากระบบ inspection แต่ละลำต้องไปดึงทีละชุด — Oracle เรียก API ให้เอง ไม่ต้อง copy-paste

```
User: "ตรวจสอบสถานะ vessel MWS-001, MWS-002, MWS-003 จากระบบ inspection ให้หน่อย"
Oracle: 🔧 กำลังดึงข้อมูล...
        ├─ MWS-001: ✅ Passed (24 Jan 2026)
        ├─ MWS-002: ⚠️ Expired (18 Dec 2025)
        └─ MWS-003: ✅ Passed (20 Jan 2026)
        ✨ สรุป: 2 ลำผ่าน, 1 ลำหมดอายุแล้วครับ
```

**จุดเด่น:** Tool-calling เป็น feature ที่ Oracle "เปิด browser/code runner" เรียก API จริง ไม่ใช่แค่ตอบจากความรู้ที่เก่า

---

### Example 3: Multi-Agent แบ่งบทบาททีม ABL

**สถานการณ์:** โปรเจกต์ใหญ่มีหลาย role เกี่ยวข้อง — Country Manager, Surveyor, Inspector แต่ละคนคนละความเชี่ยวชาญ

```
User: "จัดทีม ABL สำรวจ site ให้หน่อย"
Oracle: 🤝 แบ่งทีมให้ครับ (spawn sub-agents):

        🎯 Country Manager (คุณ):
           ├─ ดูภาพรวม budget & timeline
           └─ approve plan รวม

        📐 Surveyor (sub-agent):
           ├─ วัดพื้นที่ site
           └─ เช็ค condition ดิน/น้ำ

        🔍 Inspector (sub-agent):
           ├─ ตรวจ safety compliance
           └─ generate checklist

        ✨ ทั้งหมด sync กันผ่าน shared memory — คุณเห็นภาพรวมทุกอย่าง
```

**จุดเด่น:** Multi-agent คือการให้ AI แตกยอดเป็นทีม เชี่ยวชาญแตกต่างกัน แต่คุยกันได้

---

## 🛠️ Use Cases สายงานอื่นๆ

| Use Case | Command | Output |
|----------|---------|--------|
| เรียน codebase ใหม่ | `/learn <project>` | สรุปโครงสร้างโปรเจกต์ |
| หาไฟล์ | `/trace <pattern>` | List ไฟล์ที่ match |
| สรุป PR | `/summary #123` | Bullet points |
| ตรวจ code | `/review <file>` | Suggestions |

---

## 🚀 ลองเล่นจริง

- [Playground](/oracle-playground/playground/) — ลองสอน Oracle ให้จำคุณ
- [Comparison](/oracle-playground/comparison/) — เทียบ Copilot vs Oracle ด้วยตา

---

💡 **Tip:** เริ่มจาก [Playground](/oracle-playground/playground/) หรือ [Comparison](/oracle-playground/comparison/) เพื่อเห็นความต่างก่อนใช้จริงครับ

---

## 🚀 อยากลอง Oracle จริง เริ่มยังไง?

1. **ติดตั้ง Oracle** — ดู[การติดตั้ง](/oracle-playground/docs/install)
2. **Clone ARRA Oracle v3** — [GitHub](https://github.com/Soul-Brews-Studio/arra-oracle-v3)
3. **เข้า Discord** — [ถามตอบ community](https://discord.gg/oracle)

หรือลองเล่นใน [Playground](/oracle-playground/playground/) ก่อน — ไม่ต้องติดตั้ง!
