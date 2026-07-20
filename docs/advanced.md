---
layout: doc
title: ขั้นสูง
---

# ขั้นสูง

## 🔗 Integration

### Discord Bridge

Oracle สามารถเชื่อมกับ Discord:

```bash
oracle discord link --guild <GUILD_ID>
```

### MCP Server

ใช้เป็น MCP server สำหรับ Claude Code:

```bash
oracle mcp start
```

## 🧠 Memory Management

### ARRA/Muninn

Oracle ใช้ ARRA/Muninn เป็น external memory:

```
Record + Retrieve + Prove
```

### Search Memory

```bash
oracle memory search "keyword"
```

### Import Memory

```bash
oracle memory import file.json
```

## 🎯 Custom Skills

สร้าง skill ของตัวเอง:

```bash
oracle skill create my-skill
```

โครงสร้าง skill:
```
skills/
└── my-skill/
    ├── skill.md
    └── examples/
```

## 🔧 Debugging

### Enable Debug Mode

```bash
oracle --debug
```

### Check Status

```bash
oracle status
oracle logs tail
```

## 📊 Analytics

ดูว่าใช้อะไรไปบ้าง:

```bash
oracle gain
```

## 🚨 Troubleshooting

| ปัญหา | วิธีแก้ |
|--------|----------|
| ตอบช้า | เช็ค `oracle status` |
| Memory ไม่โหลด | ลอง `oracle memory refresh` |
| Discord ไม่ตอบ | เช็ค `oracle discord test` |

## 📖 อ่านเพิ่ม

- [GitHub: arra-oracle-v3](https://github.com/Soul-Brews-Studio/arra-oracle-v3)
