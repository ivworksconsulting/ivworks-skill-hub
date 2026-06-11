# Thai Slip Extractor

อ่านสลิปโอนเงินไทย → JSON ในขั้นตอนเดียว

รองรับ: **สลิปโอนเงินทุกธนาคาร · พร้อมเพย์ · จ่ายบิล · เติมเงิน**

---

## ตัวอย่าง

**Input:** ภาพสลิปโอนเงินจากแอปธนาคาร

**Output:**
```json
{
  "slip_type": "bank_transfer",
  "confidence": 0.95,
  "transaction": {
    "datetime": "2025-06-08T14:32:00+07:00",
    "amount": 1250.00,
    "fee": 0,
    "currency": "THB",
    "reference": "015234987654ABC"
  },
  "sender": {
    "name": "นาย ธนกร ว.",
    "bank": "กสิกรไทย",
    "account": "xxx-x-x4821-x"
  },
  "receiver": {
    "name": "น.ส. อรพรรณ ส.",
    "bank": "ไทยพาณิชย์",
    "account": "xxx-xxx512-3",
    "promptpay_id": ""
  },
  "flags": [],
  "verification_note": "ข้อมูลนี้อ่านจากภาพสลิปเท่านั้น ไม่ยืนยันว่าเงินเข้าบัญชีจริง"
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
@path/to/ivworks-skill-hub/skills/thai-slip-extractor/skill.md
```

### Copy-paste (ทุก AI tool)
1. เปิด [`skill.md`](./skill.md)
2. Copy ทั้งไฟล์
3. วางเป็น system prompt ใน Claude / ChatGPT / Gemini หรือ AI tool ที่ใช้

### Cursor / Windsurf
ดู [`guides/cursor.md`](../../guides/cursor.md)

---

## ข้อจำกัดที่ต้องรู้

⚠️ skill นี้ **อ่านข้อมูลจากภาพสลิปเท่านั้น** — ยืนยันไม่ได้ว่าเงินเข้าบัญชีจริงหรือสลิปเป็นของแท้
ใช้เพื่อช่วยบันทึก/กระทบยอดเท่านั้น การยืนยันยอดเงินต้องตรวจกับธนาคารหรือ statement เสมอ

---

## Sample Files

_ดู [`samples/`](./samples/) สำหรับภาพสลิปตัวอย่าง (สังเคราะห์ — ไม่ใช่ธุรกรรมจริง)_

---

## ต้องการ Customize?

- ต่อกับระบบบันทึกยอดขาย / บัญชีอัตโนมัติ
- ทำ batch processing สลิปหลายใบพร้อมกัน
- เชื่อม LINE OA รับสลิปจากลูกค้าอัตโนมัติ

→ [คุยกับ IV Works Consulting](https://www.ivworksconsulting.com)
