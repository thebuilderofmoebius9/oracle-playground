---
layout: doc
title: FAQ ความปลอดภัย
---

# FAQ ความปลอดภัยและความเป็นส่วนตัว

คำถามที่ผู้บริหารถามบ่อยเกี่ยวกับ Oracle Memory System

---

## 📁 ข้อมูลของฉันเก็บที่ไหน?

**คำตอบ:** เก็บบนเครื่องคุณเอง ผ่าน **localStorage** ของ browser

- ข้อมูลทั้งหมดอยู่ในเครื่องของคุณ (local-only)
- ไม่มีการส่งไป server ภายนอกโดย default
- คุณเป็นเจ้าของข้อมูล 100%

> ℹ️ **อ้างอิง:** [MDN Web Storage API — localStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage)

---

## 👥 คนอื่นเห็นข้อมูลของฉันไหม?

**คำตอบ:** **ไม่** เว้นแต่คุณเปิดเผยเอง

- localStorage เป็น **sandbox ต่อเครื่อง** — browser แต่ละเครื่องไม่แชร์กัน
- ไม่มี cloud sync โดย default (ต่อให้คุณใช้ Oracle บนหลายเครื่อง แต่ละเครื่องจำแยกกัน)
- ถ้าอยาก backup/cross-device ต้อง config เพิ่มเอง

---

## 🗑️ ลบความจำได้ไหม?

**คำตอบ:** **ได้** — มี 3 วิธี:

1. **ปุ่มล้างใน Playground** — คลิก "ล้างความจำ" ได้ทันที
2. **Browser DevTools** — ไปที่ Application → Local Storage → Remove
3. **Code** — `localStorage.clear()` หรือ `localStorage.removeItem('key')`

> ⚠️ **Caution:** ลบแล้วความจำหายไปเหลือ 0 — Oracle จะกลับมาเป็นคนแปลก

---

## 🔒 เข้ารหัส (Encryption) ไหม?

**คำตอบ:** **ไม่** โดย default — localStorage เป็น **plain text**

- ในเครื่องคุณ: ใครมี access เครื่องคุณ (และเปิด browser) อาจอ่านได้
- แต่ localStorage ไม่ถูกส่งออกเครื่อง — คนภายนอกไม่เห็น

**ถ้าอยากเข้ารหัส:**
- ต้อง config เพิ่ม (encrypt ก่อน save ใน localStorage)
- หรือใช้ secure storage solution ที่ต่อ database ของตัวเอง

---

## 🌐 Oracle ที่ฝั่ง server ส่งข้อมูลไหม?

**คำตอบ:** ขึ้นกับ config

| Mode | ข้อมูลคุยกับ AI | Memory ที่เก็บ |
|------|-------------------|-----------------|
| **Local-only** (default) | ผ่าน API provider (Anthropic/OpenAI) ตามปกติ | localStorage เครื่องคุณ |
| **Fleet / Custom** | ผ่าน server ที่คุณ host เอง | อยู่ที่ database ของคุณ |

> ℹ️ **Note:** การส่งข้อความไป AI provider (Anthropic/OpenAI) มี privacy policy แยกจาก Oracle memory system

---

## 🚨 ถ้าเครื่องถูก hack ข้อมูลหายไหม?

**คำตอบ:** **ใช่** — localStorage ไม่ปลอดภัยจากการ hack เครื่อง

- ถ้า malware/keylogger อยู่ในเครื่อง → localStorage อ่านได้
- **แนะนำ:** อย่าเก็บข้อมูล sensitive (password, token, secret) ใน Oracle memory
- Oracle เหมาะกับ context/ workflow/ preference — ไม่ใช่ vault

---

## 📝 Summary สั้นๆ

| เรื่อง | Status |
|--------|--------|
| ข้อมูลอยู่ที่ไหน | ✅ เครื่องคุณเอง (local) |
| คนภายนอกเห็นไหม | ✅ ไม่เห็น |
| ลบได้ไหม | ✅ ได้ |
| เข้ารหัสไหม | ⚠️ ไม่ (plain text) |
| ปลอดภัยจาก hack | ⚠️ ไม่ (local หายถ้าเครื่องโดน hack) |

---

## 🎯 ใช้อย่างไรให้ปลอดภัย

1. **อย่าเก็บ secret** — password, API key, private key ไม่ควรอยู่ใน Oracle memory
2. **ลบบ่อย** — ถ้าใช้เครื่องสาธารณะ/ร่วมกัน ล้าง memory ทุกครั้ง
3. **Encrypt ถ้าต้อง** — ถ้า config เอง ใส่ encryption layer เพิ่ม

---

> 📚 **อ้างอิงเพิ่ม:**
> - [MDN — Web Storage API](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage)
> - [OWASP — HTML5 Security](https://owasp.org/www-project-web-security-testing-guide/)

---

## 🚀 พร้อมลอง Oracle จริงแล้ว?

1. **ลองเล่นใน Playground** — [ไม่ต้องติดตั้ง](/oracle-playground/playground/)
2. **ติดตั้ง Oracle จริง** — [ดูวิธีติดตั้ง](/oracle-playground/docs/install)
3. **Clone ARRA Oracle v3** — [GitHub](https://github.com/Soul-Brews-Studio/arra-oracle-v3)
4. **เข้า Discord** — [ถามตอบ community](https://discord.gg/oracle)

มีข้อสงสัยเพิ่ม? ดู [Glossary](/oracle-playground/glossary/) หรือ [Oracle 101](/oracle-playground/oracle101/) ได้ครับ
