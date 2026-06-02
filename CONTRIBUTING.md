# สร้าง Skill ใหม่

## โครงสร้างของแต่ละ Skill

```
skills/
└── your-skill-name/
    ├── skill.md          ← instruction file (สิ่งที่ agent import)
    ├── README.md         ← อธิบายให้คน อ่านพร้อม example
    ├── samples/          ← ไฟล์ตัวอย่าง input (anonymized)
    │   └── README.md
    └── screenshots/      ← ภาพ output ตัวอย่าง
        └── README.md
```

## กฎของ skill.md

1. **Self-contained** — ไม่ depend on ไฟล์อื่น อ่านไฟล์เดียวแล้วใช้ได้เลย
2. **Claude-first** — optimize สำหรับ Claude แต่ต้องไม่ใช้ Claude-specific syntax ที่ทำให้ agent อื่น parse ไม่ได้
3. **มี trigger ชัดเจน** — ระบุว่า agent ควร activate skill เมื่อไหร่
4. **มี output format** — ระบุ format ของผลลัพธ์ที่คาดหวัง
5. **ภาษาไทย-friendly** — handle Thai text ได้ถูกต้อง

## Template: skill.md

```markdown
# [Skill Name]

## Trigger
[เงื่อนไขที่ agent ควร activate skill นี้]

## Purpose
[อธิบาย skill ทำอะไร ในหนึ่งประโยค]

## Behavior
[ขั้นตอนที่ agent ต้องทำ เป็น numbered list]

## Output Format
[JSON schema หรือ format ของผลลัพธ์]

## Edge Cases
[กรณีพิเศษที่ต้องระวัง]

## Examples
[Input → Output ตัวอย่าง]
```

## กฎของ README.md

- อธิบาย skill ด้วยภาษาที่ non-technical คนเข้าใจได้
- มี "วิธีใช้" ทั้งแบบ Claude, copy-paste, และ agent อื่น
- มีรูป screenshot อย่างน้อย 1 รูปจาก `screenshots/`
- มี sample file reference จาก `samples/`

## กฎของ samples/

- ไฟล์ต้องเป็น anonymized เสมอ — ลบข้อมูลจริงออกก่อน commit
- ใส่ไฟล์หลายรูปแบบถ้าเป็นไปได้ (PDF, PNG, JPEG)
- ชื่อไฟล์บอกชัดว่าเป็น document type ไหน เช่น `sample-invoice-01.pdf`

## กฎของ screenshots/

- แสดง input → output ชัดเจน
- resolution ไม่ต่ำกว่า 1200px wide
- ชื่อไฟล์เป็น `[skill-name]-[step]-[description].png`
