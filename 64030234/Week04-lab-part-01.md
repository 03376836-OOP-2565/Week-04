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

    ![Lab1.1](./Images/CodeLab1.1.png)

    ![Lab1.1](./Images/Lab1.1.png)


    1.2 Fish  เช่น ปลากัด ปลาทู ปลาแซลมอน เป็นสัตว์มีกระดูกสันหลัง อาศัยในน้ำ มี เหงือก (gills),  เกล็ด (scales)  และ ครีบ (fins)

    ![Lab1.2](./Images/CodeLab1.2.png)

    ![Lab1.2](./Images/Lab1.2.png)


    1.3 Reptiles (สัตว์เลื้อยคลาน)  เช่น จรเข้ งู กิ้งก่า เป็นสัตว์ที่มีเกล็ดบนผิวหนัง เป็นสัตว์เลือดเย็นและเกิดบนบก
    
    ![Lab1.3](./Images/CodeLab1.3.png)

    ![Lab1.3](./Images/Lab1.3.png)

    1.4 Amphibians (สัตว์ครึ่งบกครึ่งน้ำ) เช่น กบ เขียด อึ่งอ่าง เกิดในน้ำ เมื่อแรกเกิดจะหายใจด้วยเหงือกคล้ายปลา เมื่อโตขึ้นจะพัฒนาปอดขึ้นมาและอาศัยบนบกเป็นหลัก

    ![Lab1.4](./Images/CodeLab1.4.png)

    ![Lab1.4](./Images/Lab1.4.png)


    1.5 Arthropods เช่น กุ้ง ก้งกือ แมงมุม มด เป็นสัตว์ที่มีมากกว่า 4 ขา 

    ![Lab1.5](./Images/CodeLab1.5.png)

    ![Lab1.5](./Images/Lab1.5.png)

2. ให้วิเคราะห๋และเขียนคลาสไดอะแกรม แสดงการสืบทอดของยานพาหนะ ทางบก ทางน้ำ และ ทางอากาศ

![Lab2](./Images/CodeLab2.png)

![Lab2](./Images/Lab2.png)

   

3. ให้ยกตัวอย่างประเภทของที่อยู่อาศัย ให้คำจำกัดความและแสดงคลาสไดอะแกรม

![Lab3](./Images/CodeLab3.png)

![Lab3](./Images/Lab3.png)

## 2. [แผนภาพตามแนวคิด Association abstraction](Week04-lab-part-02.md)


