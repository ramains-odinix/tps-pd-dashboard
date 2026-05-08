# 🏰 TPS Production Dashboard — Hogwarts Edition

> **"After all this time?" — Always.**
> An interactive production-tracking dashboard for the TPS Digital Agency, themed as Hogwarts School of Production Wizardry.

[![Live Demo](https://img.shields.io/badge/Live-Demo-D4B144?style=for-the-badge&logo=github)](https://YOUR-USERNAME.github.io/tps-dashboard/)

---

## ✨ Features

- **6 Sidebar Sections** — Team Overview · Client Work · Team Performance · Squad View · Individual View · Insights
- **10-dimensional Filter Bar** — Year, Month, Squad, Client, Owner, Task Type, Status, Priority, Complexity, Project Type
- **House-themed Squads** — Squad 1 = Gryffindor, Squad 2 = Slytherin, Squad 3 = Ravenclaw, Squad 4 = Hufflepuff
- **Manhour Workload Logic** — 158.4 h/month full · 4 zones (Free / OK / Overload / Crisis)
- **CSV Upload (Append + Replace modes)** — drop multiple files, system accumulates data
- **Data Source Manager** — see/remove individual client uploads
- **Local Storage Persistence** — close & reopen, your data stays
- **PDF Export** — download any page as PDF
- **Fully Responsive** — fits any screen from mobile (☰ menu) to ultra-wide

---

## 🚀 Deploy to GitHub Pages — Step by Step

### Method 1 — Web UI (เร็วที่สุด, ไม่ต้องใช้ command line)

1. **Login GitHub:** ไปที่ https://github.com/login
2. **สร้าง Repository ใหม่:**
   - คลิก ปุ่ม **+** มุมขวาบน → **New repository**
   - Repository name: `tps-dashboard` (หรือชื่ออื่นที่ชอบ)
   - เลือก **Public** (GitHub Pages free ต้องใช้ public)
   - ติ๊ก **Add a README file** (จะสร้าง repo ทันที)
   - กด **Create repository**
3. **Upload ไฟล์:**
   - กดปุ่ม **Add file** → **Upload files**
   - ลาก `TPS_Production_Dashboard.html` เข้ามา
   - **เปลี่ยนชื่อไฟล์เป็น `index.html`** (สำคัญมาก!)
   - (Optional) อัปโหลด `README.md` ด้วยเลย
   - กด **Commit changes** ด้านล่าง
4. **เปิด GitHub Pages:**
   - ในหน้า repo → **Settings** (แท็บด้านบน)
   - เลื่อนเมนูซ้ายไปที่ **Pages**
   - **Source:** เลือก `Deploy from a branch`
   - **Branch:** เลือก `main` / `(root)` → **Save**
   - รอ 1-2 นาที (GitHub จะ build และ deploy)
5. **เข้าใช้งาน:**
   - URL จะเป็น: `https://YOUR-USERNAME.github.io/tps-dashboard/`
   - แชร์ลิงก์นี้ให้ทีมได้เลย

### Method 2 — Command Line (สำหรับ Dev)

```bash
# 1. ใน terminal บนเครื่อง mac
cd ~/Desktop/PD

# 2. เปลี่ยนชื่อไฟล์
cp TPS_Production_Dashboard.html index.html

# 3. Init git
git init
git add index.html README.md
git commit -m "🏰 Initial deployment of TPS Production Dashboard"

# 4. สร้าง repo บน GitHub แล้วเชื่อม
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/tps-dashboard.git
git push -u origin main

# 5. ไป Settings → Pages → Source: main branch → Save
```

### Method 3 — GitHub Desktop (GUI ง่ายๆ)

1. ดาวน์โหลด https://desktop.github.com/
2. **File → New Repository** → เลือกโฟลเดอร์ PD
3. กด **Publish repository** → เลือก Public
4. ไปที่ web ของ repo → Settings → Pages → Source: main → Save

---

## 📁 Project Structure

```
tps-dashboard/
├── index.html          # Dashboard หลัก (rename จาก TPS_Production_Dashboard.html)
├── README.md           # ไฟล์นี้
└── data/               # (Optional) CSV ตัวอย่าง — ไม่จำเป็น
    └── sample.csv
```

---

## 📊 Data Format (CSV Schema)

ไฟล์ CSV ทุกไฟล์ต้องมี header เหล่านี้ (เรียงตาม):

```csv
Priority,No,Year,Month,Project Type,Project ID,Client,Task,Task Type,Squad,Complexity,Owner,Estimated Manhour,Actual Manhour,Revise Reason,Do Date,Due Date,Actual Due Date,Diff,Task Status,Remark
```

**ค่าที่ระบบเข้าใจ:**

- **Priority:** `ด่วนที่สุด` / `กลาง` / `รอได้` / (ว่าง)
- **Squad:** `Squad 1` / `Squad 2` / `Squad 3` / `Squad 4`
- **Complexity:** `งานง่าย` / `งานกลาง` / `งานยาก`
- **Task Status:** `Doing` / `Hold` / `Client Review` / `Client Approved` / `Done`
- **Project Type:** `Operation` / `Pitching` / `Company`
- **Estimated Manhour / Actual Manhour:** ตัวเลข (ชั่วโมง)
- **Diff:** จำนวน(วัน) — ติดลบคือเลย due date

---

## 🪄 Manhour Workload Formula

- เต็ม **158.4 ชั่วโมง/เดือน** (176 hr × buffer 10%)
- **Workload = ผลรวม Estimated Manhour ของแต่ละคน**
- **Utilization = Workload / 158.4 × 100%**

| Range | Status | Action |
|-------|--------|--------|
| < 80% | 🔵 Free | ต้อง assign งานเพิ่ม |
| 80-100% | 🟢 OK | กำลังพอเหมาะ |
| 100-120% | 🟡 Overload | เริ่มเฝ้าระวัง |
| > 120% | 🔴 Crisis | ต้องลงไปช่วยทันที |

---

## 🎨 Design Credits

**Visual Direction:** Kappa (กานดา) — Chief Experience Officer  
**Theme:** Hogwarts School of Witchcraft and Wizardry (J.K. Rowling × Warner Bros.)  
**Color Palette:** Gryffindor Red `#7A0F0E` · Slytherin Green `#1E4A2C` · Ravenclaw Blue `#243763` · Hufflepuff Gold `#D4B144`  
**Typography:** Cinzel (Display) + Cormorant Garamond (Italic) + Sarabun (Body Thai)

---

## 🛠 Tech Stack

- **Vanilla JavaScript** — no build step needed
- **Chart.js 4.4** — interactive charts
- **PapaParse** — CSV parsing
- **jsPDF + html2canvas** — PDF export
- **CSS Grid + Flexbox + clamp()** — fully responsive
- **localStorage** — client-side persistence

All loaded via CDN — just open the HTML file.

---

## 📝 Updating Data

**บน GitHub Pages (online):**
- ทุกคนเปิด URL จะเห็น dashboard
- การ upload CSV จะเก็บใน **localStorage ของ browser แต่ละคน** (ไม่ sync)
- ถ้าต้องการให้ทีมเห็น data เดียวกัน — ให้ฝัง CSV ไว้ใน HTML โดยตรง (`DEFAULT_CSV` constant)

**สำหรับ Production จริง — แนะนำเพิ่ม backend:**
- Google Sheets API (อ่าน sheet ตรงๆ — แค่ 50 บรรทัด JS)
- Supabase / Firebase — database + auth
- ลองคุย Iota (The Architect) ถ้าจะทำเวอร์ชัน multi-user

---

## 🤝 Contributing

ถ้ามีฟีเจอร์ที่อยากเพิ่ม:
1. Fork repository
2. Create branch (`git checkout -b feature/amazing-feature`)
3. Commit changes
4. Open Pull Request

---

## 📄 License

MIT License — ใช้ได้ฟรี แก้ไขได้ตามใจ

---

**Made with 🪄 by TPS Production Team · Designed by Kappa**
