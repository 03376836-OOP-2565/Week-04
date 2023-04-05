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

    ![ภาพ](https://user-images.githubusercontent.com/115066278/230163092-b89d9c7c-aec5-44ef-9a49-0607e513ff62.png)

   
   1.2 แม่มีลูก
    
    ![ภาพ](https://user-images.githubusercontent.com/115066278/230163166-0b0617da-78f2-4c6a-94a1-26eb4ceaa4de.png)

   
   1.3 สามีรักภรรยา

    ![ภาพ](https://user-images.githubusercontent.com/115066278/230163193-c78e2e0f-b5a5-4645-81b5-501a4a522e6a.png)

   
   1.4 ดินสออยู่ในกระเป๋า

    ![ภาพ](https://user-images.githubusercontent.com/115066278/230163241-ecaec0c4-584c-42fe-8d52-67ce7c0d0d7c.png)

   
   1.5 นักการเมืองออกกฎหมาย

    ![ภาพ](https://user-images.githubusercontent.com/115066278/230163259-a7fc42e3-23d2-49e5-b8bf-8c7fb61c4d06.png)

   
   1.6 ทหารใส่เครื่องแบบ

    ![ภาพ](https://user-images.githubusercontent.com/115066278/230163276-bdf4ed64-fb03-4550-9746-2bf02a9f6af0.png)

   
   1.7 ประธานบริษัทบริหารกิจการ

    ![ภาพ](https://user-images.githubusercontent.com/115066278/230163300-a52e791f-fc3e-4ea0-a4fb-add9bc3c4c8d.png)

   
   1.8 กระดานดำอยู่ในห้องเรียน

    ![ภาพ](https://user-images.githubusercontent.com/115066278/230163324-2ac25e12-fff8-49a1-baf1-f45d32ecd920.png)



## [การวาดไดอะแกรมที่มีองค์ประกอบมากขึ้น](./Week04-lab-part-03.md)

