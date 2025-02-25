# My-mini-project
This is a small project for learning and practicing using hands-on data management in DataScience
## เรื่อง ( Subject ) : Pizza Sales Insights, What the Data Tells Us

## แหล่งที่มาของข้อมูล ( Data Source ) : Maven Analytics  website :

## วิธีการดำเนินการ
แบ่งการดำเนินการเป็น 2 วิธีการ คือ
1.	การจัดการและทำความสะอาดข้อมูลกับเพื่อให้ได้ data frame ที่ต้องการ
2.	การทำ Visualization เพื่อหาคำตอบหรือ Insight ตามสมมติฐานที่คาดการณ์ไว้

## วิธีการดำเนินการที่ 1 : จัดการและทำความสะอาดข้อมูลกับเพื่อให้ได้ data frame ที่ต้องการ
ดำเนินการตามไฟล์งานที่ 1 : "**CleaningCode_PizzaProject**" โดยมีหลักการโดยสรุปดังนี้

เชื่อมข้อมูลเข้าหากัน เนื่องจากเรามี dataset ย่อยที่ได้จากแหล่งข้อมูล ดังนี้ order_details.csv, orders.csv, pizza_types.csv และ pizzas.csv (โดยรายละเอียดของข้อมูลสามารถดูได้จากไฟล์ Meta Data.)

- อ่าน data frame ของ dataset ย่อยทั้ง 4 dataset เพื่อตรวจสอบข้อมูลเบื้องต้น เช่น ตรวจสอบ missing value, หา primary key และ foreign key สำหรับกระบวนการเชื่อมข้อมูลต่อไป จากการสำรวจพบว่า : ทุก data frame ไม่มีค่า missing value และทุก dataset มี primary key และ foreign key ที่เชื่อมข้อมูลเข้าด้วยกันได้จึงเชื่อมข้อมูลเข้าเป็น data frame เดียว
 	 
```python
pizza_1 = order_details.merge(orders, left_on='order_id', right_on='order_id')
pizza_2 = pizza_1.merge(pizzas, left_on='pizza_id', right_on='pizza_id')
pizza_4 = pizza_2.merge(pizza_types, left_on='pizza_type_id', right_on='pizza_type_id')
pizza_4.head(3)
```
- จัดการ Data frame ตามความต้องการด้วย method ต่างๆ เช่น rename, drop เป็นต้น
    * เปลี่ยนชื่อ column
      ```python

      ```
    * ลบ column ที่ไม่ต้องการ 
      ```python

      ```
    * สร้าง column ใหม่ตามต้องการ
      ```python

      ```
    * บันทึก data frame ที่ทำความสะอาดข้อมูลเรียบร้อยแล้วในชื่อ “pizza_transaction” เพื่อสะดวกในการทำกระบวนการถัดไป
      ```python

      ```
      
## วิธีการดำเนินการ : 2. ทำ Visualization เพื่อหาคำตอบหรือ Insight ตามสมมติฐานที่คาดการณ์ไว้
ซึ่งนำเนินการตามไฟล์งานที่ 2 : “Github_miniproject_pizza” โดยมีหลักการโดยสรุปดังนี้
### สรุปภาพรวมของร้านขาย pizza
* จากข้อมูลภาพรวมร้าน pizza ปี 2015 ที่แสดงใน card chart ทำให้ได้ information ดังนี้:
    * ยอดขายทั้งปีรวมเป็นเงิน 817,860 ดอลลาร์
    * ยอดขายเฉลี่ยเป็นเงิน 68,155 ดอลลาร์
    * จำนวนยอดสั่งซื้อรวมทั้งปี 21,350 ครั้ง
    * จำนวน pizza ที่ขายทั้งปี 49,574 ถาด
    * ร้านค้าขาย pizza ทั้งหมด 4 ประเภท
    * ร้านค้ามีเมนู pizza ทั้งหมด 32 เมนู
      
![image](https://github.com/user-attachments/assets/53e71352-3268-4ae9-bf8c-7c1185f1b3c6)

<center>
ดำเนินการตามไฟล์งานที่ 1 : "**CleaningCode_PizzaProject**" โดยมีหลักการโดยสรุปดังนี้
</center>


ตั้งคำถามเพื่อหาคำตอบ พร้อมมองหา insight
### Question 1: ยอดขายร้าน pizza น่าจะสูงที่สุดในเดือนธันวาคมใช่หรือไม่
