# คำถาม
### 1.1 int บน ESP32 ใช้กี่ไบต์?
### ตอบ int บน ESP32 ใช้ 4 ไบต์ (หรือ 32 บิต)
---
### 1.2 จากผลลัพธ์ นักศึกษาสังเกตเห็นอะไรเมื่อค่าเกินขอบเขตของ int บน ESP32?
### ตอบ เมื่อค่า เกินขอบเขต ของ int:
* ### ถ้าเกินค่ามากสุด → จะ ล้น (Overflow) → กลายเป็นเลขลบ
* ### ถ้าเกินค่าต่ำสุด → จะ ล้นกลับ (Underflow) → กลายเป็นเลขบวก
* ### ค่าจะ วนกลับ เพราะ int เก็บค่าจำกัดแค่ -2,147,483,648 ถึง 2,147,483,647
---
# คำถาม
### 2.1 float และ double บน ESP32 ใช้กี่ไบต์ตามลำดับ?
### ตอบ 
* ### float ใช้ 4 ไบต์
* ### double ก็ใช้ 4 ไบต์ เหมือนกัน (บน ESP32 ไม่มีความแม่นเพิ่มขึ้น)
---
### 2.2 นักศึกษาสังเกตเห็นความแตกต่างของความแม่นยำระหว่าง float และ double อย่างไร? สถานการณ์ใดที่คุณควรเลือกใช้ double แทน float?
### ตอบ ความแม่นยำ float และ double บน ESP32 float กับ double แม่นเท่ากัน เพราะทั้งคู่ใช้ 4 ไบต์ แสดงทศนิยมได้ประมาณ 6–7 ตำแหน่งเท่านั้น
* ### เมื่อไหร่ควรใช้ double แทน float?
* ### ถ้าอยู่บนระบบที่ double = 8 ไบต์ (ไม่ใช่ ESP32) ใช้ double เมื่อต้องการ ความแม่นยำสูง เช่น
* ### คำนวณทางวิทยาศาสตร์
* ### GPS
* ### การเงิน
* ### แต่บน ESP32 ใช้ float ก็พอเพราะ double ไม่ได้แม่นกว่าใน EPS32
---
# คำถาม
### 3 char ใช้กี่ไบต์? ค่าตัวเลข (ASCII value) มีความสัมพันธ์กับอักขระอย่างไร?
### ตอบ char ใช้ 1 ไบต์ (8 บิต) ตัวอักขระแต่ละตัวจะมี เลขประจำตัว ตาม ASCII 'Z' = 90 'z' = 122 ตัวอักษรกับเลข ASCII คือคนละหน้าตา แต่จริงๆ คือสิ่งเดียวกันในมุมของคอมพิวเตอร์
---
# คำถาม
### 4 bool ใช้กี่ไบต์? true และ false ถูกแสดงผลเป็นค่าใดบน Serial Monitor?
### ตอบ bool ใช้ 1 ไบต์ 
* ### true แสดงเป็น 1
* ### false แสดงเป็น 0
---
# คำถาม
### 5.1 ชนิดข้อมูลจำนวนเต็มแต่ละชนิด (long, long long, unsigned int, unsigned long, unsigned long long) ใช้กี่ไบต์บน ESP32?
### ตอบ

ชนิดข้อมูล | ขนาด (ไบต์) |
 ------- | ---------- |
long	| 4 ไบต์ |
long long | 8 ไบต์ |
unsigned int | 4 ไบต์ |
unsigned long | 4 ไบต์ |
unsigned long long | 8 ไบต์ |
---
### 5.2 บน ESP32, long มีขอบเขตเท่ากับ int หรือไม่? ชนิดข้อมูลใดที่คุณจะใช้หากต้องการเก็บค่าจำนวนเต็มบวกที่ใหญ่ที่สุด?
## ตอบ long มีขอบเขตเท่ากับ int (ทั้งคู่เป็น 32-bit) ใช้ unsigned long long เก็บได้สูงสุดถึงประมาณ 18,446,744,073,709,551,615 (2^64 - 1)
# คำถาม
### byte ใช้กี่ไบต์? เมื่อ myByte ถูกกำหนดให้เป็น 256 ผลลัพธ์ที่ได้คืออะไร และเพราะเหตุใด?
* ### byte ใช้กี่ไบต์? ตอบ ใช้ 1 ไบต์ (8 บิต) 
* ###  เมื่อ myByte = 256 ผลลัพธ์คืออะไร? ผลลัพธ์คือ 0
* ### byte เก็บได้แค่ 0 ถึง 255
* ### พอใส่ 256 → มัน ล้น (overflow) → วนกลับเป็น 0 (เพราะ 256 % 256 = 0)
---
# คำถาม
### คำถาม
### ทำไม 10 / 3.0 (เมื่อตัวหารเป็น float หรือ double) ถึงได้ผลลัพธ์เป็นทศนิยม แต่เมื่อตัวหารถูกแปลงเป็น int แล้วผลลัพธ์เป็นจำนวนเต็ม?
### ตอบ เพราะชนิดข้อมูลที่ใช้คำนวณมีผลกับผลลัพธ์
* ### 10 / 3.0 → มี float หรือ double อยู่ → คอมพิวเตอร์จะคำนวณแบบ ทศนิยม → ได้ 3.33...
* ### 10 / (int)3.0 → ทั้งสองเป็น int → คอมพิวเตอร์จะคำนวณแบบ จำนวนเต็ม → ทศนิยม ถูกตัดทิ้ง → ได้ 3
---
# คำถาม
### นักศึกษาจะใช้การทำ Type Casting ในสถานการณ์ใดบ้างในการเขียนโปรแกรม?
### ตอบ นักศึกษาควรใช้ Type Casting เมื่อ
### 1.ต้องการเปลี่ยนชนิดข้อมูล เช่น
* ### แปลง float เป็น int เพื่อตัดทศนิยม
* ### แปลง char เป็น int เพื่อดูค่า ASCII
### 2.ต้องการให้ผลลัพธ์ถูกต้อง เช่น
* ### หารเลขให้ได้ทศนิยม ต้องแปลงอย่างน้อยตัวหนึ่งเป็น float หรือ double
### 3.ป้องกันการคำนวณแบบจำนวนเต็มที่ตัดทศนิยม
* ### ต้องการบังคับให้ตัวแปรแปลงเป็นชนิดที่ต้องการ เพื่อให้โปรแกรมทำงานถูกต้องหรือแม่นยำ
---

