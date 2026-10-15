# คำอธิบายข้อมูล (Data Description)

เอกสารนี้อธิบายรายละเอียดชุดข้อมูลที่ใช้ในโครงงาน **E-commerce Sales Analytics**

---

## 1. แหล่งที่มาและสิทธิ์การใช้ข้อมูล

| หัวข้อ | รายละเอียด |
| --- | --- |
| **ชื่อชุดข้อมูล** | E-commerce Sales Analytics |
| **แหล่งที่มาเดิม** | https://www.kaggle.com/datasets/abbas829/ecommerce-sales-dataset |
| **ประเภทข้อมูล** | ข้อมูลการขายสินค้าแบบ 1 แถวต่อ 1 คำสั่งซื้อ (Order-level data) |

---

## 2. ไฟล์ในโครงงาน

| ตำแหน่งไฟล์ | คำอธิบาย |
| --- | --- |
| `C:\Users\User\Desktop\viewweiv\ecommerce\data\ecommerce_sales_analytics_5000.csv` | ไฟล์ข้อมูลดิบ (Raw Data) มีทั้งหมด 5,000 แถว 12 คอลัมน์ **ห้ามแก้ไขด้วยมือ** |
| `C:\Users\User\Desktop\viewweiv\ecommerce\data\processed\sales_clean.csv` | ข้อมูลที่ผ่านการทำความสะอาดและตรวจสอบแล้ว 5,000 แถว **สร้างจาก** `code/01_clean_data.py` หรือสมุดโน้ต `ecommerce_sales_analysis.ipynb` |

> **วิธีประมวลผลข้อมูลใหม่:** วางไฟล์ดิบไว้ที่ตำแหน่ง `data/ecommerce_sales_analytics_5000.csv` แล้วรันสคริปต์ Python ในไฟล์ `code/01_clean_data.py` หรือรันเซลล์ในไฟล์ `ecommerce_sales_analysis.ipynb`

---

## 3. พจนานุกรมข้อมูล (Data Dictionary) ของ `sales_clean.csv`

ข้อมูลหลังทำความสะอาดมีทั้งหมด **5,000 แถว 12 คอลัมน์** รายละเอียดแต่ละคอลัมน์มีดังนี้:

| คอลัมน์ | ชนิดข้อมูล | คำอธิบาย / ค่าที่เป็นไปได้ | จำนวนค่าว่าง |
| --- | --- | --- | ---: |
| `order_id` | ตัวเลข (Integer) | รหัสคำสั่งซื้อ (ช่วงค่าตั้งแต่ 10001 ถึง 15000) | 0 |
| `order_date` | วันที่ (Datetime/String) | วันที่ทำรายการสั่งซื้อ (รูปแบบ `YYYY-MM-DD` หรือ `M/D/YYYY`) | 0 |
| `customer_id` | ตัวเลข (Integer) | รหัสประจำตัวลูกค้า (ช่วงค่าตั้งแต่ 1000 ถึง 1999) | 0 |
| `product_category` | ข้อความ (String) | หมวดหมู่สินค้า ได้แก่ `Beauty`, `Clothing`, `Electronics` และ `Home` | 0 |
| `region` | ข้อความ (String) | ภูมิภาคที่จัดส่ง ได้แก่ `North`, `South`, `East` และ `West` | 0 |
| `quantity` | ตัวเลข (Integer) | จำนวนสินค้าที่สั่งซื้อต่อรายการ (1 ถึง 7 ชิ้น) | 0 |
| `unit_price` | ตัวเลข (Float) | ราคาสินค้าต่อหน่วย (สกุลเงิน USD) | 0 |
| `discount` | ตัวเลข (Float) | อัตราส่วนลดสินค้า (ค่าระหว่าง 0.00 ถึง 0.35 หรือ 0% ถึง 35%) | 0 |
| `payment_method` | ข้อความ (String) | ช่องทางการชำระเงิน ได้แก่ `Card`, `COD` (เก็บเงินปลายทาง) และ `Wallet` | 0 |
| `delivery_days` | ตัวเลข (Integer) | ระยะเวลาการจัดส่งสินค้า (1 ถึง 11 วัน) | 0 |
| `customer_rating` | ตัวเลข (Float) | คะแนนความพึงพอใจจากลูกค้า (คะแนนตั้งแต่ 1.0 ถึง 5.0) | 0 |
| `revenue` | ตัวเลข (Float) | ยอดขายสุทธิรวมหลังหักส่วนลด คำนวณจาก `quantity * unit_price * (1 - discount)` | 0 |

---

## 4. หมายเหตุเพิ่มเติม

1. **สกุลเงิน:** จำนวนเงินทั้งหมดในคอลัมน์ `unit_price` และ `revenue` มีหน่วยเป็น **ดอลลาร์สหรัฐ (USD)**
2. **ความถูกต้องของข้อมูล:** ยอดขายสุทธิ (`revenue`) ถูกตรวจสอบด้วยสูตร $Revenue = Quantity \times UnitPrice \times (1 - Discount)$ แล้ว
