# ivworks-skill-hub — Project Context for Claude

## What This Is

GitHub repo ที่รวม AI agent skills สำหรับงานธุรกิจ สร้างโดย IV Works Consulting
Claude-first แต่ออกแบบให้ใช้กับ agent ไหนก็ได้ (Cursor, Windsurf, copy-paste)

ดู website: https://www.ivworksconsulting.com

---

## โครงสร้าง Repo

```
ivworks-skill-hub/
├── agents.md               ← central registry — import file เดียวได้ทุก skill
├── CONTRIBUTING.md         ← standard และ template สำหรับสร้าง skill ใหม่
├── guides/                 ← วิธีใช้กับ Cursor, Windsurf, etc.
└── skills/
    └── [skill-name]/
        ├── skill.md        ← instruction file จริง (สิ่งที่ agent import)
        ├── README.md       ← อธิบาย + example + วิธีใช้ (สำหรับคนอ่าน)
        ├── samples/        ← input files ตัวอย่าง (anonymized เสมอ)
        └── screenshots/    ← ภาพ input→output demo
```

---

## Skills ที่มีอยู่

| Skill | สถานะ |
|---|---|
| `thai-document-extractor` | ✅ skill.md พร้อม — รอ samples + screenshots |

---

## Convention ที่ต้องรู้

**skill.md ต้อง:**
- Self-contained — ไม่ depend on ไฟล์อื่น
- มี Trigger, Purpose, Behavior, Output Format, Edge Cases
- Handle Thai text ได้ถูกต้อง (ตัวเลขไทย, วันที่พุทธศักราช)
- ไม่ใช้ Claude-specific syntax ที่ทำให้ agent อื่น parse ไม่ได้

**samples/ ต้อง:**
- Anonymized เสมอก่อน commit — ลบข้อมูลจริงออก

**agents.md ต้อง update ทุกครั้งที่เพิ่ม skill ใหม่**

ดูรายละเอียดทั้งหมดใน `CONTRIBUTING.md`

---

## เป้าหมาย

- skills เป็น lead magnet → ดึง developer + Thai SME มาเจอ IV Works
- distribution หลักผ่าน GitHub + เว็บ ivworksconsulting.com (Skill Hub section)
- paid path: ผู้ใช้อยากได้ custom skill หรือ integrate กับระบบ → จ้าง IV Works

---

## สิ่งที่ Claude ช่วยได้

- เขียน skill.md ใหม่ตาม CONTRIBUTING.md template
- ทดสอบ skill กับ sample files
- update agents.md เมื่อเพิ่ม skill
- เขียน README.md ของแต่ละ skill
