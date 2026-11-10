# NakhonPhanom Local – ชุดเริ่มต้น

โครงสร้าง: index.html (หน้าแอป LIFF) · functions/api/me.js (ตรวจล็อกอิน LINE) · supabase/schema.sql (ตาราง + RLS)

## ขั้นตอน (ฟรีทั้งหมด)
1. **Supabase**: สร้างโปรเจกต์ > SQL Editor > วางไฟล์ supabase/schema.sql > Run
   จากนั้นไปที่ Project Settings > API จดค่า Project URL, anon key (เปิดเผยได้) และ service_role key (ลับ!)
2. **ใส่ค่าใน index.html** ตรง CONFIG: SUPABASE_URL และ SUPABASE_ANON_KEY (ห้ามใส่ service_role key)
3. **GitHub**: สร้าง repo ใหม่ แล้วอัปโหลดไฟล์ทั้งหมดในโฟลเดอร์นี้ (คงโครงสร้างโฟลเดอร์ไว้)
4. **Cloudflare Pages**: Workers & Pages > Create > Pages > Connect to Git > เลือก repo
   Build command: เว้นว่าง · Output directory: / (หรือเว้นว่าง) แล้ว Deploy
   ที่ Settings > Variables and Secrets (Production) เพิ่ม 3 ค่า:
   LINE_CHANNEL_ID = 2012500542 · SUPABASE_URL · SUPABASE_SERVICE_KEY (ชนิด Secret)
   แล้ว Redeploy 1 ครั้ง
5. **LINE Developers**: แท็บ LIFF > แก้ Endpoint URL เป็นลิงก์ https://....pages.dev ที่ได้
6. เปิด https://liff.line.me/2012500542-i4u4YU9r จากมือถือเพื่อทดสอบ (ช่องยังเป็น Developing ใช้ได้เฉพาะผู้ดูแล/ผู้ทดสอบ)

## เพิ่มข้อมูลสถานที่ทดสอบ
Supabase > Table Editor > places > Insert row: ใส่ category_id (เช่น cafe), name_th, address, price_from และตั้ง status = approved

## หมายเหตุ
- ชื่อหมวดภาษาลาวและข้อความลาวในแอปเป็นร่างจากผม ควรให้เจ้าของภาษาตรวจ
- ฟอนต์หัวข้อเป็นตัวทดแทน (Thasadith, Bebas Neue) จนกว่าจะได้รับอนุญาตใช้ฟอนต์ต้นฉบับ
- Channel ID ได้จากเลขหน้า LIFF ID ถ้าไม่ตรง ให้ดูที่แท็บ Basic settings ของช่อง LINE Login
