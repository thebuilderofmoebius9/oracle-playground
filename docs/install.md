---
layout: doc
title: การติดตั้ง
---

# การติดตั้ง Oracle

## 📋 ข้อกำหนด (Prerequisites)

- Node.js 18+ หรือ Docker
- GitHub account (ถ้าใช้ GitHub-hosted)
- หน้าว่าง 200MB สำหรับติดตั้ง

## 🚀 วิธีติดตั้ง

### แบบง่าย — Docker

```bash
docker run -d --name oracle \
  -v ~/oracle-data:/data \
  -p 3000:3000 \
  soul-brews/oracle:latest
```

### แบบ Developer — จาก source

```bash
# Clone repo
git clone https://github.com/Soul-Brews-Studio/arra-oracle-v3.git
cd arra-oracle-v3

# Install dependencies
npm install

# Setup
npm run setup

# Start
npm start
```

## ✅ ตรวจสอบการติดตั้ง

```bash
oracle --version
oracle status
```

ถ้าเห็น version และ status = "ready" แสดงว่าพร้อมใช้งาน!

## 🐛 ปัญหาที่เจอบ่อย

| ปัญหา | วิธีแก้ |
|--------|----------|
| Port 3000 ใช้ไม่ได้ | เปลี่ยน port: `oracle start --port 3001` |
| Memory เต็ม | เพิ่ม swap หรือใช้ `--low-memory` |
| Permission denied | ใช้ `sudo` หรือ fix permission |

## 📖 ต่อไป

- [คำสั่งพื้นฐาน](/oracle-playground/docs/basic)
