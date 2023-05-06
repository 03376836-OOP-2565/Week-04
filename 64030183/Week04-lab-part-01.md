# การทดลอง วาดไดอะแกรมด้วย plantUML (2)


## 1. แผนภาพตามแนวคิด generalization abstraction

### 1.1 คลาสของสัตว์

#### 1.1.1 Mammals

- Dogs, cats, horses, duckbill platypuses, kangaroos, dolphins และ whales เป็นสัตว์เลี้ยงลูกด้วยนม
- ตัวอ่อนดื่มนมเป็นอาหาร และมีขนตามร่างกาย

#### วิเคราะห์คลาสหลัก Mammals 
Attributes 
- สีขน
- อายุ
- เพศ

Methods
 - กินอาหาร
 - เคลื่อนที่

``` plantuml
@startuml
class Mammal
{
    + color
    - age
    - gender
    + eat()
    + move()
}
@enduml
```

![](./Lab/Pictures/pict-01.png)


####  คลาสย่อย


``` plantuml
@startuml
class Dogs
class cats
class horses
class platypuses
class kangaroos
class dolphins
class whales
@enduml
```

![](./Lab/Pictures/pict-02.png)


#### การแสดงความสัมพันธ์ generalization

ทำได้โดยการใช้เครื่องหมายลูกศรสามเหลี่ยม หรือเขียนเป็นสัญลักษณ์ด้วย code ดังตัวอย่างด้านล่างนี้

``` plantuml
@startuml
"Base class" <|-- "Inherited class"
@enduml
```

### ตัวอย่างระบบคลาสของ mammals

``` plantuml
@startuml 
class Mammal
{
    + color
    - age
    - gender
    + eat()
    + move()
}

class Dogs
class cats
class horses
class platypuses
class kangaroos
class dolphins
class whales

Mammal <|-- Dogs
Mammal <|-- cats
Mammal <|-- horses
Mammal <|-- platypuses
Mammal <|-- kangaroos
Mammal <|-- dolphins
Mammal <|-- whales
@enduml
```

![](./Lab/Pictures/pict-03.png)


## แบบฝึกหัด 
ให้เขียนคลาสไดอะแกรมของหัวข้อต่อไปนี้ โดยใช้ plantuml


1. ให้นักศึกษาวาดไดอะแกรมของการ inheritance ของสัตว์ให้ครบทุกประเภท โดยเพิ่ม properties และ methods ได้ตามคำอธิบายหรือธรรมชาติของสัตว์ชนิดนั้นๆ 

    1.1  Birds เช่น เหยี่ยว ห่าน เป็ด ไก่ มีขน และเกิดจากไขที่มีเปลือกแข็ง ขนบนปีกและหาง จะทับซ้อนกันอยู่ ซึ่งทำให้โต้ลม และทำให้นกบินและร่อนลงได้

![image](https://user-images.githubusercontent.com/115066431/236636205-cda3125a-a9c1-4f83-b66d-2e7eb9827bf9.png)


    1.2 Fish  เช่น ปลากัด ปลาทู ปลาแซลมอน เป็นสัตว์มีกระดูกสันหลัง อาศัยในน้ำ มี เหงือก (gills),  เกล็ด (scales)  และ ครีบ (fins)
    
![image](https://user-images.githubusercontent.com/115066431/236636238-6c595aaa-4a3e-491c-8030-c4030e5e9ab2.png)


    1.3 Reptiles (สัตว์เลื้อยคลาน)  เช่น จรเข้ งู กิ้งก่า เป็นสัตว์ที่มีเกล็ดบนผิวหนัง เป็นสัตว์เลือดเย็นและเกิดบนบก
 
 ![image](https://user-images.githubusercontent.com/115066431/236636268-3dab967c-dcd6-4f62-aea6-966b0292b762.png)


    1.4 Amphibians (สัตว์ครึ่งบกครึ่งน้ำ) เช่น กบ เขียด อึ่งอ่าง เกิดในน้ำ เมื่อแรกเกิดจะหายใจด้วยเหงือกคล้ายปลา เมื่อโตขึ้นจะพัฒนาปอดขึ้นมาและอาศัยบนบกเป็นหลัก
    
 ![image](https://user-images.githubusercontent.com/115066431/236636292-1aa46e84-4968-4deb-85ca-f4d8fd8d895e.png)


    1.5 Arthropods เช่น กุ้ง ก้งกือ แมงมุม มด เป็นสัตว์ที่มีมากกว่า 4 ขา 
    
 ![image](https://user-images.githubusercontent.com/115066431/236636328-420ff497-e954-48a2-bcf4-b46f4a401330.png)


2. ให้วิเคราะห๋และเขียนคลาสไดอะแกรม แสดงการสืบทอดของยานพาหนะ ทางบก ทางน้ำ และ ทางอากาศ

![image](https://user-images.githubusercontent.com/115066431/236637505-5b16ce6c-7512-4b81-9abe-47a1a5e0d1e1.png)


3. ให้ยกตัวอย่างประเภทของที่อยู่อาศัย ให้คำจำกัดความและแสดงคลาสไดอะแกรม

![image](https://user-images.githubusercontent.com/115066431/236637632-b895108d-747f-452e-97cd-c8b7f2246964.png)


## 2. [แผนภาพตามแนวคิด Association abstraction](Week04-lab-part-02.md)


