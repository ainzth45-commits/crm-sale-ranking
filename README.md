# SALE RANKING — Dashboard ขึ้นจอ TV

Dashboard อันดับยอดขายแบบ realtime (ธีมดำ-ทอง) + ระบบเสียงพากย์แซว (TTS) สำหรับเปิดบนจอ TV ออฟฟิศ
เว็บ static ดึงข้อมูลสดจาก Supabase (anon key + RLS anon-read, ไม่มี PII)

## 🔗 ลิงก์เปิดเว็บ (GitHub Pages)

| หน้า | ลิงก์ |
|------|-------|
| **จอจริง (ขึ้น TV)** | https://ainzth45-commits.github.io/crm-sale-ranking/ |
| **หน้าทดสอบฟังเสียง** (audition 220 ข้อ) | https://ainzth45-commits.github.io/crm-sale-ranking/test.html |

> หน้าจอจริงมีปุ่ม **"เปิดใช้งาน"** ต้องกดก่อนเสียงถึงจะเล่นได้ (browser ปลดล็อก autoplay)

## 📁 ไฟล์

- `index.html` — Dashboard จอจริง (อันดับ 1 ใหญ่ + 2/3 ซ้าย, 4-10 scroll ขวา, timer, ลูกเล่น FX, เสียงพากย์)
- `test.html` — หน้า audition ฟังเสียง taunts ทั้ง 220 ข้อ แยกหมวด + สลับเพศเสียง

## 🔊 ระบบเสียง

- Edge Function `tts` (เสียงไทย neural Premwadee หญิง / Niwat ชาย) + cache ใน Storage
- ข้อความแซวเก็บใน Supabase ตาราง `taunts` (220 ข้อ, 5 หมวด) — **แก้/เพิ่มใน DB ได้เลยไม่ต้อง deploy ใหม่**
- ความทนทาน: retry สูงสุด 2 ครั้ง → ถ้า edge-tts ล่ม/autoplay บล็อก → fallback เป็น Web Speech ของเบราว์เซอร์ (ได้ยินเสมอ)

## 🗂️ Repo

https://github.com/ainzth45-commits/crm-sale-ranking

## ⚙️ อัปเดตเว็บ

แก้ไฟล์ในโฟลเดอร์นี้ แล้ว:

```bash
cd "supabase/Dashboard"
git add -A && git commit -m "ข้อความ commit"
git push
```

GitHub Pages จะ rebuild อัตโนมัติภายใน ~1 นาที
