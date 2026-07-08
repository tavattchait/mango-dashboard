# Dashboard บริหารโครงการ — GitHub Pages mirror

Static copy of the dashboard frontend, ทำงานอิสระจาก Google Apps Script (ไม่ต้องล็อกอิน Google เพื่อดู ไม่มีแถบเทา "แอปสร้างโดยผู้ใช้ Google Apps Script")

## โครงสร้าง
- `index.html` — หน้า Dashboard บริหารโครงการ (เดิมคือ Index.html)
- `investor.html` — หน้า Investor Dashboard (เดิมคือ Investor.html)

ทั้งสองไฟล์ดึงข้อมูลจริงผ่าน `fetch()` ไปที่ Apps Script Web App เดิม (deployment เดียวกับที่ใช้อยู่ทุกวันนี้ ไม่ได้แตะ) แทนที่ `google.script.run` ที่ใช้ได้แค่ตอน served จาก Apps Script เอง — ดู `window.APPS_SCRIPT_API_URL` ใน `<script>` บล็อกแรกของแต่ละไฟล์

## แก้โค้ด/อัปเดตข้อมูลใหม่ ทำยังไง
1. แก้ที่ `mango-dashboard2/Code.js` ตามปกติ (backend, ยังอยู่ที่ Apps Script เดิม) แล้ว `clasp push` + `clasp deploy -i <deployment id เดิม>` เหมือนเดิมทุกอย่าง — ฝั่ง GitHub Pages จะได้ข้อมูลใหม่ทันทีเพราะเรียก API เดียวกัน
2. แก้ดีไซน์/เลย์เอาต์หน้าเว็บ → แก้ตรง `index.html`/`investor.html` ในโฟลเดอร์นี้เลย แล้ว commit + push ขึ้น GitHub, Pages จะอัปเดตเองภายในไม่กี่นาที

## Deploy ครั้งแรก (ทำครั้งเดียว)
ดูขั้นตอนในแชทที่ Claude อธิบายไว้ หรือสรุปสั้นๆ:
1. สร้าง repo ใหม่บน github.com (public หรือ private ก็ได้ — Pages ใช้ได้ทั้งคู่ถ้าเป็น GitHub Free แบบ public, private ต้อง GitHub Pro ขึ้นไป)
2. `git init && git add . && git commit -m "initial" && git remote add origin <repo url> && git push -u origin main`
3. Settings → Pages → Source: "Deploy from a branch" → Branch: `main` / `(root)` → Save
4. รอ 1-2 นาที แล้วเปิด URL ที่ GitHub ให้มา (รูปแบบ `https://<username>.github.io/<repo>/`)
