# 🚀 Quick Deploy Guide — 5 นาทีเสร็จ

## ขั้นตอนสำคัญที่สุด

⚠️ **ก่อน upload — ต้อง rename ไฟล์เป็น `index.html`**
GitHub Pages ใช้ `index.html` เป็นหน้าแรกอัตโนมัติ

วิธีง่ายๆ บน Mac:
1. Right-click `TPS_Production_Dashboard.html` → **Duplicate**
2. Rename copy ที่ได้เป็น `index.html`
3. Upload `index.html` ขึ้น GitHub

---

## 5-Minute Deploy (ง่ายสุด, ไม่ต้องใช้ Terminal)

### Step 1 — สมัคร / Login GitHub
- ไปที่ https://github.com (ฟรี — ใช้แค่ email + password)

### Step 2 — สร้าง Repository
- มุมขวาบน กด **+** → **New repository**
- **Repository name:** `tps-dashboard` (หรือชื่อที่ต้องการ)
- **Description:** `TPS Production Dashboard — Hogwarts Edition`
- เลือก **Public** ✅
- ติ๊ก **Add a README file**
- กด **Create repository**

### Step 3 — Upload ไฟล์
- ในหน้า repo → กด **Add file** (ปุ่มสีเขียวขวาบน) → **Upload files**
- ลาก **`index.html`** (ที่ rename มาแล้ว) เข้ามา
- ลาก `README.md` เข้ามาด้วย (จะ overwrite ของเดิม — กด keep our version ก็ได้)
- ที่ commit message พิมพ์: `Initial deploy of dashboard`
- กด **Commit changes**

### Step 4 — เปิด GitHub Pages
- ในหน้า repo → กด tab **Settings** (ด้านบน)
- เลื่อนเมนูซ้ายลงไปหา **Pages**
- ใต้ **Source** → เลือก **Deploy from a branch**
- ใต้ **Branch** → เลือก `main` และ `/ (root)` → กด **Save**

### Step 5 — รอ 1-2 นาที แล้วเปิด URL
- URL จะเป็น: **`https://YOUR-USERNAME.github.io/tps-dashboard/`**
- เช็คได้ใน Settings → Pages — จะมีกล่องเขียว "Your site is live at..."
- คัดลอก URL ส่งให้ทีมได้เลย ✅

---

## หลังจาก Deploy แล้ว

### อยากแก้ไข Dashboard?
1. กลับเข้า repo บน GitHub
2. คลิกที่ `index.html` → กดไอคอน ✏️ Edit
3. แก้ไข แล้ว Commit changes
4. รอประมาณ 30 วินาที — site update อัตโนมัติ

### อยากให้ทีมใช้ data ชุดเดียวกัน?
ตอนนี้ data CSV ที่ user upload จะเก็บใน browser ของตัวเองเท่านั้น
ถ้าอยากให้ทีมเห็น data ชุดเดียวกัน:
- **Option A:** อัปเดต `DEFAULT_CSV` ใน HTML แล้ว push ใหม่
- **Option B:** เชื่อม Google Sheets API — ต้องเขียน JS เพิ่ม
- **Option C:** ใช้ Supabase / Firebase — มี backend จริง

ถ้าจะทำ Option B หรือ C → คุยกับ Iota (The Architect)

---

## Troubleshooting

### ❌ "404 Not Found"
- เช็คว่าไฟล์ชื่อ `index.html` (ไม่ใช่ `TPS_Production_Dashboard.html`)
- เช็คว่า branch ที่ deploy คือ `main` (ไม่ใช่ `master`)

### ❌ Dashboard load แต่ไม่ขึ้นข้อมูล
- เปิด DevTools (F12) → Console — มี error อะไรบอกมาเลย
- ส่วนใหญ่เป็นเรื่อง CDN — ถ้ามี Firewall บล็อก อาจต้องโหลด library local

### ❌ บางคนเปิดเห็น data ของอีกคน
- เป็นเรื่อง browser localStorage — ไม่ได้ sync ข้าม device
- นี่คือพฤติกรรมที่ design ไว้ ถ้าจะ sync ต้องมี backend

---

## URL Alternative — ถ้าไม่อยากใช้ username ตัวเอง

### Custom Domain ฟรี:
1. หา domain จาก https://www.namecheap.com/ (~ $1-10/year)
2. ใน GitHub → Settings → Pages → Custom domain → ใส่ domain
3. ตั้ง DNS A records ตามที่ GitHub บอก

### หรือ ใช้ GitHub Organization:
สมัคร org account ฟรี → ใช้ URL เป็น `https://your-org.github.io/tps-dashboard/`

---

🪄 พร้อมแล้ว — ให้ทุกคนได้เข้าใช้ Hogwarts Dashboard ของทีม!
