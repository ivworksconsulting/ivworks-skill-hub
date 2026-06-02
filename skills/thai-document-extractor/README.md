# Thai Document Extractor

แปลงเอกสารธุรกิจไทยให้เป็น JSON ในขั้นตอนเดียว

รองรับ: **ใบแจ้งหนี้ · ใบเสร็จรับเงิน · ใบสั่งซื้อ · ใบเสนอราคา · ใบส่งสินค้า**

---

## ตัวอย่าง

**Input:** ภาพหรือ PDF ใบแจ้งหนี้

**Output:**
```json
{
  "document_type": "invoice",
  "confidence": 0.95,
  "document": {
    "number": "INV-2567-0042",
    "date": "2024-03-15",
    "due_date": "2024-04-14"
  },
  "issuer": {
    "name": "บริษัท ตัวอย่าง จำกัด",
    "tax_id": "0105566012345",
    "branch": "สำนักงานใหญ่"
  },
  "items": [
    {
      "description": "พัฒนาระบบ API",
      "quantity": 1,
      "unit": "งาน",
      "unit_price": 50000,
      "total": 50000
    }
  ],
  "summary": {
    "subtotal": 50000,
    "vat_amount": 3500,
    "grand_total": 53500,
    "currency": "THB"
  },
  "flags": [],
  "validation": {
    "items_sum_matches_subtotal": true,
    "vat_calculation_correct": true
  }
}
```

---

## วิธีใช้

### Claude (วิธีที่ 1 — import ผ่าน agents.md)
เพิ่มใน `CLAUDE.md`:
```markdown
@path/to/ivworks-skill-hub/agents.md
```

### Claude (วิธีที่ 2 — import skill เดี่ยว)
เพิ่มใน `CLAUDE.md`:
```markdown
@path/to/ivworks-skill-hub/skills/thai-document-extractor/skill.md
```

### Copy-paste (ทุก AI tool)
1. เปิด [`skill.md`](./skill.md)
2. Copy ทั้งไฟล์
3. วางเป็น system prompt ใน Claude / ChatGPT / Gemini หรือ AI tool ที่ใช้

### Cursor / Windsurf
ดู [`guides/cursor.md`](../../guides/cursor.md)

---

## Screenshots

_ดู [`screenshots/`](./screenshots/) สำหรับตัวอย่าง input/output จริง_

---

## Sample Files

_ดู [`samples/`](./samples/) สำหรับไฟล์เอกสารตัวอย่าง (anonymized)_

---

## ต้องการ Customize?

- รองรับ format เอกสารเฉพาะของระบบคุณ
- เชื่อมต่อกับ database หรือ ERP โดยตรง
- ทำ batch processing หลายไฟล์พร้อมกัน

→ [คุยกับ IV Works Consulting](https://www.ivworksconsulting.com)
