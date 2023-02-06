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

   <img width="745" alt="Screenshot 2566-02-06 at 20 49 09" src="https://user-images.githubusercontent.com/115066261/216988241-9120a14d-f2dc-4ae5-8df2-11e342a6022d.png">

   1.2 แม่มีลูก

   <img width="848" alt="Screenshot 2566-02-06 at 20 51 46" src="https://user-images.githubusercontent.com/115066261/216988938-c4853841-7c57-4639-94a5-a1556705a063.png">

   1.3 สามีรักภรรยา
   
   <img width="744" alt="Screenshot 2566-02-06 at 20 56 44" src="https://user-images.githubusercontent.com/115066261/216990138-50dfb3d5-7730-465e-b321-7fd3e25cc23a.png">

   1.4 ดินสออยู่ในกระเป๋า
   
   <img width="725" alt="Screenshot 2566-02-06 at 21 21 48" src="https://user-images.githubusercontent.com/115066261/216996036-d146d232-d02e-4115-bbb6-8b602f9e357b.png">

   1.5 นักการเมืองออกกฎหมาย
   
   <img width="760" alt="Screenshot 2566-02-06 at 21 05 07" src="https://user-images.githubusercontent.com/115066261/216992048-6520f272-fac7-4fc4-921d-390aa1609251.png">

   1.6 ทหารใส่เครื่องแบบ
   
   <img width="740" alt="Screenshot 2566-02-06 at 21 09 25" src="https://user-images.githubusercontent.com/115066261/216993021-94934c40-0bb2-4bc6-b535-f04d3321d491.png">

   1.7 ประธานบริษัทบริหารกิจการ
   
   <img width="829" alt="Screenshot 2566-02-06 at 21 17 10" src="https://user-images.githubusercontent.com/115066261/216994876-ac76dac2-afc5-492f-a701-c6538a3c6ef0.png">

   1.8 กระดานดำอยู่ในห้องเรียน

<img width="768" alt="Screenshot 2566-02-06 at 21 20 14" src="https://user-images.githubusercontent.com/115066261/216995625-a97ef856-963d-4ac7-b907-a2804ab5d798.png">

## [การวาดไดอะแกรมที่มีองค์ประกอบมากขึ้น](./Week04-lab-part-03.md)

