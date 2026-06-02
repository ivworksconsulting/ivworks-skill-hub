# Thai Document Extractor

_Skill by IV Works Consulting — ivworksconsulting.com_

## Trigger

Activate เมื่อผู้ใช้:
- ส่งภาพหรือ PDF เอกสารธุรกิจไทย
- พูดถึง "ใบแจ้งหนี้", "ใบเสร็จ", "ใบสั่งซื้อ", "ใบเสนอราคา", "ใบส่งสินค้า"
- ขอให้ "extract", "อ่าน", "แปลง" หรือ "ดึงข้อมูล" จากเอกสาร

## Purpose

แปลงเอกสารธุรกิจไทยให้เป็น JSON ที่นำไปใช้ต่อได้ทันที รองรับ: ใบแจ้งหนี้, ใบเสร็จรับเงิน, ใบสั่งซื้อ, ใบเสนอราคา, ใบส่งสินค้า

## Behavior

1. **ระบุประเภทเอกสาร** — invoice / receipt / purchase_order / quotation / delivery_note / unknown
2. **Extract header fields** — เลขที่เอกสาร, วันที่, ผู้ออก, ผู้รับ, ที่อยู่, เลขภาษี
3. **Extract line items** — รายการสินค้า/บริการ ราคาต่อหน่วย จำนวน รวม
4. **Extract totals** — ยอดก่อน VAT, VAT (7%), ยอดสุทธิ, เงินมัดจำ, ยอดค้างชำระ
5. **Flag ปัญหา** — ฟิลด์ที่อ่านไม่ออก, ตัวเลขไม่สอดคล้องกัน, ข้อมูลขาด
6. **ตรวจสอบความสอดคล้อง** — คำนวณยืนยันว่า line items รวมกันตรงกับ total

## Output Format

```json
{
  "document_type": "invoice | receipt | purchase_order | quotation | delivery_note | unknown",
  "confidence": 0.0,
  "document": {
    "number": "",
    "date": "YYYY-MM-DD",
    "due_date": "YYYY-MM-DD | null"
  },
  "issuer": {
    "name": "",
    "address": "",
    "tax_id": "",
    "branch": ""
  },
  "recipient": {
    "name": "",
    "address": "",
    "tax_id": "",
    "branch": ""
  },
  "items": [
    {
      "description": "",
      "quantity": 0,
      "unit": "",
      "unit_price": 0,
      "discount": 0,
      "total": 0
    }
  ],
  "summary": {
    "subtotal": 0,
    "discount_total": 0,
    "vat_rate": 0.07,
    "vat_amount": 0,
    "grand_total": 0,
    "deposit": 0,
    "balance_due": 0,
    "currency": "THB"
  },
  "flags": [
    {
      "field": "",
      "issue": "unreadable | missing | inconsistent",
      "detail": ""
    }
  ],
  "validation": {
    "items_sum_matches_subtotal": true,
    "vat_calculation_correct": true
  }
}
```

## Edge Cases

- **ตัวเลขไทย** — แปลง ๑๒๓ เป็น 123 ก่อนใส่ output
- **วันที่พุทธศักราช** — แปลง พ.ศ. เป็น ค.ศ. ใน date fields (เช่น 2567 → 2024)
- **VAT included vs excluded** — ระบุใน flags ถ้าไม่ชัดเจน
- **ไม่มี VAT** — ให้ vat_amount: 0 และ vat_rate: 0
- **หลายหน้า** — รวม items จากทุกหน้า ใช้ total จากหน้าสุดท้าย
- **ภาพไม่ชัด** — ให้ confidence ต่ำ และ flag ฟิลด์ที่ไม่แน่ใจ

## Response Style

- ส่ง JSON block ก่อนเสมอ
- สรุปสั้น ๆ หลัง JSON ว่าพบปัญหาอะไรบ้าง (ถ้ามี)
- ถ้า confidence < 0.7 ให้แจ้งและขอภาพที่ชัดกว่า
