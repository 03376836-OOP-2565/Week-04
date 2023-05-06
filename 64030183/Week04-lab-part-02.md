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
   
   ![image](https://user-images.githubusercontent.com/115066431/236637954-d8df492d-bb1a-413f-8fa0-c41a3263f45d.png)

   
   1.2 แม่มีลูก


   ![image](https://user-images.githubusercontent.com/115066431/236638297-a73655cb-1a35-4788-bd69-2ca4464435f9.png)

   
   1.3 สามีรักภรรยา

![image](https://user-images.githubusercontent.com/115066431/236638344-bda2826f-ee7f-43fd-aaf3-018e9f1654af.png)

   
   1.4 ดินสออยู่ในกระเป๋า
   
   ![image](https://user-images.githubusercontent.com/115066431/236638378-89c035f9-d661-43b8-b0c3-8476c82004b5.png)

   
   1.5 นักการเมืองออกกฎหมาย
   
   ![image](https://user-images.githubusercontent.com/115066431/236638418-c75f6c05-c267-4f6e-91f4-3d7bc190febb.png)

   
   1.6 ทหารใส่เครื่องแบบ
   
   ![image](https://user-images.githubusercontent.com/115066431/236638472-b8cd2717-cf31-46b1-851b-62876edc1bc2.png)

   
   1.7 ประธานบริษัทบริหารกิจการ
   
   ![image](https://user-images.githubusercontent.com/115066431/236638511-4264a18c-a19a-41c2-bfa7-d9ac3cf3f580.png)

   
   1.8 กระดานดำอยู่ในห้องเรียน
   
   ![image](https://user-images.githubusercontent.com/115066431/236638799-a8872d28-1dab-4e2c-9580-b1eff69d3e04.png)



## [การวาดไดอะแกรมที่มีองค์ประกอบมากขึ้น](./Week04-lab-part-03.md)

