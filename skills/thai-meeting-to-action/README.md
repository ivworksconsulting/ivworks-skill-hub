# Thai Meeting to Action

บันทึกประชุมไทยที่จดมาดิบ ๆ → สรุป + action items ที่มีเจ้าภาพและกำหนดส่งชัดเจน

รองรับ: **โน้ตประชุม · transcript · ภาพถ่ายบันทึก**

---

## ตัวอย่าง

**Input:** ภาพหรือข้อความบันทึกประชุม เช่น

> "ฝนรับไปทำ artwork ชุดแรก ส่งให้ดูศุกร์นี้ / หน้าโปรโมชั่นบนเว็บต้องอัปเดต — เดี๋ยวค่อยดูว่าใครว่าง"

**Output:**
```json
{
  "action_items": [
    {
      "task": "ทำ artwork ชุดแรกของแคมเปญ 11.11 ส่งให้ทีมดู",
      "owner": "ฝน",
      "due": "2025-06-13",
      "due_text": "ศุกร์นี้",
      "priority": "high"
    },
    {
      "task": "อัปเดตหน้าโปรโมชั่นบนเว็บก่อนเปิดแคมเปญ",
      "owner": null,
      "due": null,
      "due_text": "ก่อนเปิดแคมเปญ",
      "priority": "medium"
    }
  ],
  "flags": [
    {
      "item": "อัปเดตหน้าโปรโมชั่นบนเว็บก่อนเปิดแคมเปญ",
      "issue": "no_owner",
      "detail": "ที่ประชุมบอกแค่ 'เดี๋ยวค่อยดูว่าใครว่าง' ยังไม่มีคนรับผิดชอบ"
    }
  ]
}
```

จุดสำคัญ: แปลง "ศุกร์นี้" เป็นวันที่จริงจากวันประชุม, แยกเรื่องที่ตัดสินใจแล้วออกจากเรื่องค้าง,
และ **flag งานที่ไม่มีเจ้าภาพ** แทนที่จะเดา assign ให้ใครเอง

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
@path/to/ivworks-skill-hub/skills/thai-meeting-to-action/skill.md
```

### Copy-paste (ทุก AI tool)
1. เปิด [`skill.md`](./skill.md)
2. Copy ทั้งไฟล์
3. วางเป็น system prompt ใน Claude / ChatGPT / Gemini หรือ AI tool ที่ใช้

### Cursor / Windsurf
ดู [`guides/cursor.md`](../../guides/cursor.md)

---

## Sample Files

_ดู [`samples/`](./samples/) สำหรับภาพบันทึกประชุมตัวอย่าง (สังเคราะห์ — ไม่ใช่การประชุมจริง)_

---

## ต้องการ Customize?

- ส่ง action items เข้า Notion / Trello / ClickUp อัตโนมัติ
- สรุปจากไฟล์เสียงประชุม (ถอดเสียง + สรุปในขั้นตอนเดียว)
- แจ้งเตือนเจ้าภาพผ่าน LINE เมื่อใกล้ deadline

→ [คุยกับ IV Works Consulting](https://www.ivworksconsulting.com)
