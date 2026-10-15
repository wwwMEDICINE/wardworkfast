# wardworkfast

เว็บบอร์ดราวน์วอร์ดที่ทั้งทีมแก้ไขร่วมกัน (standalone web, ไม่ต้องสมัครสมาชิก)

- ตารางตามเลขเตียง: ชื่อย่อ อายุ/เพศ วัน admit (D1, D2…) และ Diagnosis
- Vital signs ล่าสุด (T, BP, HR, RR, SpO₂, O₂, DTX, เวลา) ค่าผิดปกติขึ้นสีแดงอัตโนมัติ
- Lab สำคัญ (1 บรรทัดต่อ 1 ค่า ขึ้นต้นด้วย `!` = ผิดปกติ)
- Active problems, ward work checklist, สถานะ D/C, consult panel แยกตามแผนก
- ปุ่มแชร์ลิงก์ทีม (มี QR code), สรุปส่งเวร / LINE, เริ่มราวน์วันใหม่

## การเข้าถึง
แต่ละบอร์ดมีลิงก์ลับ (`…/#<รหัส 32 ตัว>`) ใครมีลิงก์ก็ดูและแก้ไขได้ทันที หน้าแรกไม่มีข้อมูลผู้ป่วย
ใช้เลขเตียงและชื่อย่อเท่านั้น อย่าใส่ชื่อเต็ม HN หรือเลขบัตรประชาชน

## โครงสร้าง
- `index.html` ทั้งแอปอยู่ในไฟล์เดียว เรียก Supabase ผ่าน RPC (`ww_*`)
- ข้อมูลอยู่ใน Supabase project `wordworkfast` (ชื่อเดิมของ project) (schema `app` ซึ่ง API เข้าถึงตรงๆ ไม่ได้) ทุก RPC ต้องใช้รหัสบอร์ด
- โฮสต์บน GitHub Pages แบบ static (Settings → Pages → Deploy from a branch → `main` / root)
