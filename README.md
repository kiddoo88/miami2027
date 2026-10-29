# Coastline · Miami & Florida Keys 2027

เว็บแอปส่วนตัวสำหรับทริป 16–24 มกราคม 2027: Miami, Florida Keys, Key West, Dry Tortugas, Everglades และประชุมที่ Fontainebleau Miami Beach ไม่มี Disney

## เปิดใช้งาน

ไม่ต้องติดตั้ง dependencies หรือ build โปรเจกต์ ใช้ static web server จากโฟลเดอร์โปรเจกต์ เช่น:

```sh
python3 -m http.server 4173
```

เปิด http://localhost:4173 ในเบราว์เซอร์รุ่นปัจจุบัน อย่าเปิด index.html ด้วย file:// เพราะแอปใช้ JavaScript modules

## อัปโหลดเข้า GitHub

1. แตกไฟล์ `miami-keys-github.zip` ก่อน
2. สร้าง repository หรือเปิด repository ที่ต้องการใน GitHub
3. เลือก **Add file → Upload files** แล้วลากไฟล์และโฟลเดอร์ด้านในทั้งหมดเข้าไป รวมโฟลเดอร์ `assets`
4. ให้ `index.html` อยู่ระดับบนสุดของ repository (ไม่อยู่ใต้โฟลเดอร์ซ้อน)
5. เลือก **Commit changes** เพื่อบันทึกไฟล์

อัปโหลดไฟล์ที่แตกออกมา ไม่ใช่อัปโหลด ZIP เพียงไฟล์เดียว หากตัวเลือก Upload files ไม่แสดงไฟล์ที่ขึ้นต้นด้วยจุด สามารถเพิ่ม `.nojekyll` และ `.gitignore` ผ่าน **Add file → Create new file** ได้ภายหลัง เว็บนี้ไม่มีไฟล์ที่ขึ้นต้นด้วย `_` จึงใช้งานได้แม้ไม่ได้เพิ่ม `.nojekyll`

## เปิดเป็นเว็บด้วย GitHub Pages

1. ไปที่ **Settings → Pages** ของ repository
2. ใน **Build and deployment → Source** เลือก **Deploy from a branch**
3. เลือก branch ที่อัปโหลดไฟล์ เช่น `main` และโฟลเดอร์ **/(root)** แล้วกด **Save**
4. รอให้ GitHub เผยแพร่เสร็จ แล้วเปิด URL ที่แสดงในหน้า Pages

ใช้ relative asset paths ทั้งหมด จึงรองรับ URL แบบ `https://USERNAME.github.io/REPOSITORY/` ไม่ต้องแก้ base URL และไม่ต้องตั้งค่า API key, environment variable หรือ npm build

GitHub Pages ฉบับนี้ไม่มีระบบล็อกอินของ Sites โดยทั่วไปหน้าเว็บที่เผยแพร่เข้าถึงได้สาธารณะ ข้อมูลเริ่มต้นในซอร์สจะแสดงบนเว็บ ส่วนโน้ตและค่าใช้จ่ายที่เพิ่มภายหลังเก็บในเบราว์เซอร์ของแต่ละคน

การตั้งค่า Pages อาจขึ้นอยู่กับสิทธิ์และแพ็กเกจของ repository: [คู่มือ GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)

เผยแพร่บน static hosting อื่นได้เช่นกัน โดยเลือกโฟลเดอร์นี้เป็นโฟลเดอร์เว็บไซต์

## ฟีเจอร์

- Overview พร้อมวันที่ เส้นทาง นับถอยหลัง และความคืบหน้าการจอง
- Timeline ทั้ง 9 วัน: เพิ่ม แก้ไขเวลา/รายละเอียด เลื่อนลำดับ ลบ และทำเครื่องหมายว่าเสร็จแล้ว
- โน้ตรายวันพร้อมปุ่มบันทึก
- Photo spots พร้อมตัวกรองพื้นที่ หัวใจรายการโปรด และลิงก์ Google Maps
- แผนที่พัก 8 คืน: Miami 1 / Key West 2 / Homestead 1 / Fontainebleau 4
- Booking checklist 10 รายการ พร้อมสถานะ เลขยืนยัน และโน้ต
- Budget tracker: งบรวม งบตามหมวด ค่าใช้จ่ายจริง USD/THB และอัตราแลกเปลี่ยนที่กำหนดเอง
- เก็บข้อมูลด้วย localStorage และรับการอัปเดตจากอีกแท็บในเบราว์เซอร์เดียวกัน
- ส่งออก/นำเข้าไฟล์ JSON พร้อมตรวจรูปแบบและยืนยันก่อนแทนที่แผน
- Responsive navigation, keyboard focus, native dialogs, reduced-motion support

## การย้ายข้อมูลจากเว็บเดิม

หากเคยแก้แผนบนเว็บ Sites เดิม ให้ส่งออก JSON จากเว็บเดิม แล้วนำเข้าในเว็บ GitHub Pages เนื่องจากข้อมูล localStorage แยกตามที่อยู่เว็บไซต์ การอัปโหลดซอร์สนี้ไม่ได้ย้ายข้อมูลที่บันทึกในเบราว์เซอร์ไปด้วย

## ข้อมูลและข้อจำกัด

ข้อมูลเริ่มต้นทั้งหมดมีสถานะยังไม่ได้จอง/ยืนยัน ไม่มีการจอง ชำระเงิน หรือส่งข้อมูลให้ผู้ให้บริการจากแอปนี้ เวลาบินมาจากผู้เดินทาง ส่วนเวลาเที่ยวและขับรถเป็นแผนโดยประมาณ เวลาประชุมยังต้องยืนยันกับกำหนดการจริง

Dry Tortugas วันที่ 18 ม.ค. 2027 ยังไม่ได้ตรวจสอบที่นั่ง มีแผนสำรองใน Key West กรณีไม่มีที่นั่งหรือเรือยกเลิก ข้อมูลสถานที่อ้างอิงเว็บไซต์ทางการที่ตรวจเมื่อ 28 ต.ค. 2026 ต้องตรวจซ้ำก่อนเดินทาง

ข้อมูลส่วนตัวเก็บบนอุปกรณ์/เบราว์เซอร์/ที่อยู่เว็บเดียวกัน ไม่มีบัญชีหรือ cloud sync การเปิดลิงก์เดียวกันบนอีกเครื่องจะเริ่มจากแผนเริ่มต้น หากต้องการย้ายข้อมูลให้ส่งออกแล้วนำเข้าไฟล์ JSON การล้างข้อมูลเบราว์เซอร์อาจทำให้แผนหาย ควรสำรองเป็นระยะ

USD เป็นหน่วยงบหลัก อัตราตั้งต้น 35 THB/USD เป็นตัวเลขสมมติที่แก้ไขได้ ไม่ใช่อัตราสด รายการ THB จะคำนวณใหม่เมื่อเปลี่ยนอัตรา ไม่มีราคาที่พัก/เรือ/เที่ยวบินที่เสนอขายจริงในแอป

ไม่ได้รองรับ offline แบบ PWA การเปิดหน้าเว็บครั้งแรกและลิงก์แผนที่/แหล่งข้อมูลต้องใช้อินเทอร์เน็ต ภาพหลักอยู่ในโปรเจกต์ ส่วนฟอนต์เสริมโหลดจาก Google Fonts และมี system fallback

## โครงสร้าง

- `index.html` — โครงหน้าแอป
- `style.css` — ดีไซน์และ responsive breakpoints
- `data.js` — แผนตั้งต้น สถานที่ ที่พัก รายการจอง และแหล่งข้อมูล
- `app.js` — หน้าจอ ฟอร์ม การคำนวณ และ local persistence
- `assets/` — ภาพสถานที่
- `.nojekyll` — ใช้ไฟล์เว็บโดยตรงบน GitHub Pages
- `.gitignore` — ข้ามไฟล์ระบบและไฟล์ข้อมูลสำรองส่วนตัว
- `QA.md` — ผลทดสอบและวิธีตรวจซ้ำ

## แหล่งภาพ

ภาพใช้เพื่อบรรยากาศ ไม่ใช่ภาพห้องพักที่จองหรือรับประกันมุมถ่ายจริง:

- Overseas Highway / Seven Mile Bridge: https://unsplash.com/photos/RWJxrQ4WZ2g (asset photo-1740989973080-95c282ab1b16)
- Miami: https://images.unsplash.com/photo-1514214246283-d427a95c5d2f
- Fort Jefferson: National Park Service — https://www.nps.gov/articles/coastal-geohazards-storm-surges.htm
- Anhinga Trail: USGS — https://www.usgs.gov/media/images/florida-everglades-national-park-1

แหล่งข้อมูลท่องเที่ยวทางการอยู่ในหน้า Bookings → แหล่งข้อมูลและสิ่งที่ควรตรวจอีกครั้ง
