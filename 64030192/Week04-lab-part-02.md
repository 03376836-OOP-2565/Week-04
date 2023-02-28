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

   1.1 คนเป็นเจ้าของรถยนต์<br>
   ![image](https://user-images.githubusercontent.com/115066298/221880501-3e5e2436-ec72-4abc-b9bd-6689d511c8db.png)

   
   1.2 แม่มีลูก<br>
   ![image](https://user-images.githubusercontent.com/115066298/221880591-34e3809e-fff9-4b74-8a02-7dba4753ed2d.png)

   
   1.3 สามีรักภรรยา<br>
   ![image](https://user-images.githubusercontent.com/115066298/221881064-af204c55-627f-41fb-baa5-fac17a96a374.png)

   
   1.4 ดินสออยู่ในกระเป๋า<br>
   ![image](https://user-images.githubusercontent.com/115066298/221881131-0f3e207f-0ef0-4224-b88b-ee70d9caced6.png)

   
   1.5 นักการเมืองออกกฎหมาย<br>
   ![image](https://user-images.githubusercontent.com/115066298/221881231-25960b1e-3200-422c-a24e-1d717da76ac1.png)

   
   1.6 ทหารใส่เครื่องแบบ<br>
   ![image](https://user-images.githubusercontent.com/115066298/221881289-e3aa5859-0dcc-401b-8136-f752366f7b15.png)

   
   1.7 ประธานบริษัทบริหารกิจการ<br>
   ![image](https://user-images.githubusercontent.com/115066298/221881361-4b9d56e4-9d95-40fc-9169-beb5391885de.png)

   
   1.8 กระดานดำอยู่ในห้องเรียน<br>
   ![image](https://user-images.githubusercontent.com/115066298/221881423-f49a0b49-d213-4763-a780-be8d8e51bb9f.png)



## [การวาดไดอะแกรมที่มีองค์ประกอบมากขึ้น](./Week04-lab-part-03.md)

