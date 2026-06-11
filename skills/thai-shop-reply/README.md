# Thai Shop Reply

ข้อความลูกค้า → จับ intent + ร่างคำตอบสุภาพแบบร้านค้าออนไลน์มืออาชีพ

รองรับ: **ถามราคา · เช็คสต็อก · ตามออเดอร์ · ตำหนิ/เคลม · ขอคืนเงิน**

---

## ตัวอย่าง

**Input:** ข้อความหรือภาพแชทจากลูกค้า เช่น

> "สั่งเซรั่มไปตั้งแต่วันจันทร์ ของยังไม่ถึงเลยค่ะ 😤 ถ้าส่งไม่ทันวันเสาร์ขอคืนเงินได้มั้ยคะ"

**Output:**
```json
{
  "intent": "order_status",
  "sentiment": "negative",
  "urgency": "high",
  "summary": "ลูกค้าตามออเดอร์ที่ยังไม่ถึง มี deadline วันเสาร์ ถ้าไม่ทันขอคืนเงิน",
  "reply_polite": "สวัสดีค่ะ ทางร้านต้องขออภัยอย่างยิ่งนะคะ... เลขพัสดุของคุณลูกค้าคือ [เลขพัสดุ] ...",
  "reply_casual": "ขอโทษจริง ๆ นะคะ 🙏 เดี๋ยวแม่ค้าเช็คกับขนส่งให้ด่วนเลยค่ะ...",
  "missing_info": ["เลขพัสดุ", "สถานะพัสดุล่าสุด", "เงื่อนไขการคืนเงินของร้าน"],
  "suggested_actions": ["เช็คสถานะกับขนส่งทันทีก่อนตอบ", "อย่ารับปากคืนเงินก่อนเช็คนโยบายร้าน"]
}
```

จุดสำคัญ: skill **ไม่แต่งข้อเท็จจริง** — ราคา เลขพัสดุ เงื่อนไขคืนเงิน ที่ไม่รู้จริงจะเป็น placeholder `[...]` พร้อม list ใน `missing_info` ให้เติมก่อนส่ง

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
@path/to/ivworks-skill-hub/skills/thai-shop-reply/skill.md
```

### Copy-paste (ทุก AI tool)
1. เปิด [`skill.md`](./skill.md)
2. Copy ทั้งไฟล์
3. วางเป็น system prompt ใน Claude / ChatGPT / Gemini หรือ AI tool ที่ใช้

### Cursor / Windsurf
ดู [`guides/cursor.md`](../../guides/cursor.md)

---

## Sample Files

_ดู [`samples/`](./samples/) สำหรับภาพแชทตัวอย่าง (สังเคราะห์ — ไม่ใช่บทสนทนาจริง)_

---

## ต้องการ Customize?

- ปรับ tone ให้ตรงกับแบรนด์ของร้าน
- ต่อกับ LINE OA / Facebook ตอบลูกค้าอัตโนมัติ
- ดึงสต็อก/ราคาจริงจากระบบมาเติม placeholder ให้อัตโนมัติ

→ [คุยกับ IV Works Consulting](https://www.ivworksconsulting.com)
