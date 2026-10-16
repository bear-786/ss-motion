# วิธี Deploy เว็บเสนอญัตติ สส.

เว็บนี้เป็น **Pure HTML/CSS/JS** ไม่ต้องการ server จึง deploy ได้ง่ายๆ บน Netlify หรือ Vercel

---

## ✅ ขั้นตอนที่ 1 — ตั้งค่า Discord Webhook URL

1. เปิดไฟล์ `index.html` ด้วย VS Code หรือ Notepad
2. หาบรรทัดนี้ (ใกล้ท้ายไฟล์):
   ```js
   const DISCORD_WEBHOOK_URL = "YOUR_DISCORD_WEBHOOK_URL_HERE";
   ```
3. แทนที่ `YOUR_DISCORD_WEBHOOK_URL_HERE` ด้วย Webhook URL จริง เช่น:
   ```js
   const DISCORD_WEBHOOK_URL = "https://discord.com/api/webhooks/1234567890/xxxx...";
   ```

### วิธีสร้าง Discord Webhook
1. เปิด Discord → เข้า Server ที่ต้องการ
2. คลิกขวาที่ Channel → **Edit Channel**
3. ไปที่ **Integrations** → **Webhooks** → **New Webhook**
4. ตั้งชื่อ เช่น "ระบบญัตติ สส."
5. คลิก **Copy Webhook URL**

---

## 🚀 ขั้นตอนที่ 2 — Deploy บน Netlify (แนะนำ / ฟรี)

### วิธี Drag & Drop (ง่ายที่สุด)
1. ไปที่ [app.netlify.com](https://app.netlify.com) และ Log in
2. คลิก **Add new site** → **Deploy manually**
3. ลาก folder `ญัญติ สส` ทั้งหมดไปวาง
4. ✅ เสร็จ! ได้ URL เช่น `https://amazing-name-123.netlify.app`

### วิธีกำหนด Custom Domain
- ใน Netlify → Site settings → Domain management → Add custom domain

---

## 🚀 Deploy บน Vercel (ทางเลือก)

1. ไปที่ [vercel.com](https://vercel.com) → Log in
2. **Add New Project** → Import จาก GitHub, หรือใช้ Vercel CLI:
   ```bash
   npx vercel --yes
   ```

---

## 🛡️ หมายเหตุด้านความปลอดภัย

> **ข้อควรระวัง**: Webhook URL ในไฟล์ HTML จะมองเห็นได้จาก Source Code ของเว็บ  
> ถ้าต้องการความปลอดภัยสูงขึ้น ให้ใช้ **Netlify Functions** หรือ **Vercel Edge Functions** เป็น proxy แทน

---

## 📁 โครงสร้างไฟล์

```
ญัญติ สส/
├── index.html        ← ไฟล์หลัก (เว็บทั้งหมดอยู่ที่นี่)
└── README.md         ← ไฟล์นี้
```

---

## ✨ ฟีเจอร์ที่มี

- 📝 ฟอร์มเสนอญัตติ (ชื่อ, พรรค, ประเภท, วันที่, ชื่อญัตติ, รายละเอียด)
- 📋 แสดงรายการญัตติที่เสนอแล้วทั้งหมด
- 💬 กล่อง Confirm ก่อนส่ง
- 📨 ส่งแจ้งเตือนไปยัง Discord อัตโนมัติ (Embed Card สวยงาม)
- 💾 บันทึกข้อมูลใน localStorage (เก็บในเบราว์เซอร์)
- 📱 Responsive รองรับมือถือ
- 🎨 ธีมสีน้ำเงิน-ทอง สไตล์รัฐสภา
