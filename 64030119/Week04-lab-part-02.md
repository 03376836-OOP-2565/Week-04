# การทดลอง วาดไดอะแกรมด้วย plantUML (2)


## 2. แผนภาพตามแนวคิด Association abstraction

Association abstraction เป็นการแสดงความสัมพันธ์ระหว่าง class ที่มีความสัมพันธ์แบบเกี่ยวพันกัน ไม่สามารถอธิบายโดย Abstraction แบบอื่น ๆ ได้
- ไม่ใช่ "Is a" แบบ Classification
- ไม่ใช่ "Is part of" แบบ Aggregation
- ไม่ใช่ "Is kind of" แบบ Generalization
- แต่เป็น "Is related to"  


### รูปแบบ
``` plantuml
@startuml
"Class A" -- "Class B" :  relationship
"Class C" -- "Class D" : > relationship
"Class E" -- "Class F" : < relationship
@enduml
```

![](./Lab/Pictures/pict-04.png)


### ตัวอย่าง

1. คนเป็นเจ้าของรถยนต์

``` plantuml
@startuml
class Car
class Person
Car -- Person : < owns
@enduml
```

![](./Lab/Pictures/pict-05.png)


## Cardinality ใน Association Abstraction

“Cardinality”  คือตัวเลขที่ใช้แสดงจำนวนของสมาชิกที่สามารถมีได้ใน Class หนึ่งๆ ที่มีส่วนร่วมใน Association

### ตัวอย่าง 
แม่สามารถมีลูกได้ตั้งแต่ 0 คน ถึงกี่คนก็ได้ ในทางกลับกัน ลูก 1 คน สามารถมีแม่ได้เพียงคนเดียว

![](./Lab/Pictures/pict-06.png)


ขั้นตอนที่ 1 : เขียน class 2 class ที่มีความสัมพันธ์และลากเส้นตรงใส่ชื่อแสดงความสัมพันธ์

``` plantuml
@startuml
class Mom
{
    - Attribues
    + Method()
}

class Son
{
    - Attribues
    + Method()
}

Mom - Son : has
@enduml
``` 
จะได้ผลลัพธ์ดังรูป

![](./Lab/Pictures/pict-07.png)

หรือจะละไว้ในกรณีที่ไม่ต้องการแสดงรายละเอียดภายในคลาสก็ได้ ดังตัวอย่าง

``` plantuml
@startuml
Mom - Son : has
@enduml
```

จะได้ผลลัพธ์ดังรูป

![](./Lab/Pictures/pict-08.png)

ขั้นตอนที่ 2 : เขียนลูกศรเพื่อแสดงทิศทางของการอ่านความสัมพันธ์ให้ถูกต้อง

``` plantuml
@startuml
Mom - Son : > has
@enduml
```

จะได้ผลลัพธ์ดังรูป

![](./Lab/Pictures/pict-09.png)


ขั้นตอนที่ 3 : พิจารณา class ที่อยู่ติดกับหัวลูกศรว่ามีความสัมพันธ์กับ class แรกด้วย min-card และ max-card เป็นเท่าใด

``` plantuml
@startuml
Mom - "0..n" Son : > has
@enduml
```

จะได้ผลลัพธ์ดังรูป

![](./Lab/Pictures/pict-10.png)


ขั้นตอนที่ 4 : พิจารณา class ที่อยู่ติดกับหัวลูกศรว่ามีความสัมพันธ์กับ class แรกด้วย min-card และ max-card เป็นเท่าใด จนกระทั่งได้ภาพที่สมบูรณ์

``` plantuml
@startuml
Mom "1..1" - "0..n" Son : > has
@enduml
```

จะได้ผลลัพธ์ดังรูป

![](./Lab/Pictures/pict-11.png)
 

### หมายเหตุ

เราสามารถควบคุมทิศทางการวาดคลาสไดอะแกรมได้โดยการเปลี่ยนเครื่องหมาย `-` เป็น `--` ดังตัวอย่าง

โดยจำนวนที่เพิ่มขึ้นของ `-` จะมีส่วนเพิ่มระยะห่างระหว่างคลาสด้วย 


``` plantuml
@startuml
Mom "1..1" - "0..n" Son : > has
Person "1..1" -- "0..n" Car : > has
Forest "1..1" --- "0..n" tree : > has
@enduml
```

จะได้ผลลัพธ์ดังรูป

![](./Lab/Pictures/pict-12.png)




##  แบบฝึกหัด

1. จงเขียนความสัมพันธ์ในโลกของความเป็นจริง ให้เป็น association diagram โดยเพิ่ม cardinality และ กำหนดทิศทางความสัมพันธ์ให้ถูกต้อง

   1.1 คนเป็นเจ้าของรถยนต์
   ![image](https://user-images.githubusercontent.com/115066285/232197647-54294818-a8da-41da-bed3-9caebad05720.png)

   1.2 แม่มีลูก
   ![image](https://user-images.githubusercontent.com/115066285/232198083-123a65f0-dc87-4e1d-9800-2a293cd520e3.png)

   1.3 สามีรักภรรยา
   ![image](https://user-images.githubusercontent.com/115066285/232198447-5af74cdd-54ce-48ea-8430-03369f8ce275.png)

   1.4 ดินสออยู่ในกระเป๋า
   ![image](https://user-images.githubusercontent.com/115066285/232198649-c63060a8-67cf-4f29-859c-92e64124e7c2.png)

   1.5 นักการเมืองออกกฎหมาย
   ![image](https://user-images.githubusercontent.com/115066285/232198856-4a6a6d18-7ee3-4065-bfda-554d7d098bb6.png)

   1.6 ทหารใส่เครื่องแบบ
   ![image](https://user-images.githubusercontent.com/115066285/232198944-c70c34aa-3d37-4f8d-bf3c-b1895179aa80.png)

   1.7 ประธานบริษัทบริหารกิจการ
   ![image](https://user-images.githubusercontent.com/115066285/232199182-7817b96e-4751-4d0d-9a00-8b100cacf4bc.png)

   1.8 กระดานดำอยู่ในห้องเรียน
![image](https://user-images.githubusercontent.com/115066285/232199231-52d40fa3-c993-4cdc-a91a-7aa7857cc83c.png)


## [การวาดไดอะแกรมที่มีองค์ประกอบมากขึ้น](./Week04-lab-part-03.md)

