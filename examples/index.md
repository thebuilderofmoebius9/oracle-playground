---
layout: doc
title: ตัวอย่าง
---

# ตัวอย่างการใช้งาน

## 💬 สนทนา

### Example 1: ถามเรื่องการ setup

```
User: อยาก setup PostgreSQL ใน Docker ยังไง?
Oracle: [วิธีพร้อม docker-compose.yml และคำอธิบาย]
```

### Example 2: วิเคราะห์ code

```
User: วิเคราะห์ฟังก์ชันนี้หน่อย
[แปะ code]
Oracle: [อธิบาย logic, ชี้ bug, เสนอการปรับปรุง]
```

## 🛠️ งานจริง

### Example 3: สร้าง CRUD API

```
User: สร้าง Express API สำหรับ manage todos
Oracle: [สร้างไฟล์ routes, controllers, models]
```

### Example 4: Debug

```
User: มี bug ตรงนี้ ช่วยดูหน่อย
[แสดง error log]
Oracle: [วิเคราะห์หาสาเหตุ + แนวทางแก้]
```

## 🎯 Use Cases

| Use Case | Command | Output |
|----------|---------|--------|
| เรียน codebase ใหม่ | `/learn <project>` | สรุปโครงสร้าง |
| หาไฟล์ | `/trace <pattern>` | List ไฟล์ |
| สรุป PR | `/summary #123` | Bullet points |
| ตรวจ code | `/review <file>` | Suggestions |

## 📝 Next.js Example

```javascript
// app/api/oracle/route.js
export async function POST(req) {
  const { message } = await req.json();
  const response = await oracle.chat(message);
  return Response.json(response);
}
```

## 🚀 ลองเล่น

ไปที่ [Playground](/oracle-playground/playground/) เพื่อลองจริง!
