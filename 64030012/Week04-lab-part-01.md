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
![Screenshot 2023-04-09 193914](https://user-images.githubusercontent.com/115066186/230774276-a65cddc2-f4b9-4cc0-871f-03b4b1d6d625.png)

    1.2 Fish  เช่น ปลากัด ปลาทู ปลาแซลมอน เป็นสัตว์มีกระดูกสันหลัง อาศัยในน้ำ มี เหงือก (gills),  เกล็ด (scales)  และ ครีบ (fins)
![Screenshot 2023-04-09 194219](https://user-images.githubusercontent.com/115066186/230774280-4cd13369-f3df-424a-841c-a3e13ef360b1.png)

    1.3 Reptiles (สัตว์เลื้อยคลาน)  เช่น จรเข้ งู![Screenshot 2023-04-09 194444](https://user-images.githubusercontent.com/115066186/230774291-b45b7b1e-eff5-4495-8d05-298c86fdf5b4.png)
 กิ้งก่า เป็นสัตว์ที่มีเกล็ดบนผิวหนัง เป็นสัตว์เลือดเย็นและเกิดบนบก
![Uploading Screenshot 2023-04-09 194444.png…]()

    1.4 Amphibians (สัตว์ครึ่งบกครึ่งน้ำ) เช่น กบ เขียด อึ่งอ่าง เกิดในน้ำ เมื่อแรกเกิดจะหายใจด้วยเหงือกคล้ายปลา เมื่อโตขึ้นจะพัฒนาปอดขึ้นมาและอาศัยบนบกเป็นหลัก
![Screenshot 2023-04-09 194734](https://user-images.githubusercontent.com/115066186/230774295-d7502b20-3202-4fed-b255-474f5ac8565c.png)

    1.5 Arthropods เช่น กุ้ง ก้งกือ แมงมุม มด เป็นสัตว์ที่มีมากกว่า 4 ขา 

2. ให้วิเคราะห๋และเขียนคลาสไดอะแกรม แสดงการสืบทอดของยานพาหนะ ทางบก ทางน้ำ และ ทางอากาศ
![Screenshot 2023-04-09 195655](https://user-images.githubusercontent.com/115066186/230774298-1268137a-2386-44fc-947f-4846b190d627.png)
![Screenshot 2023-04-09 195709](https://user-images.githubusercontent.com/115066186/230774300-f33548a5-7c43-47f3-817e-683e2e04c158.png)

3. ให้ยกตัวอย่างประเภทของที่อยู่อาศัย ให้คำจำกัดความและแสดงคลาสไดอะแกรม
!![Screenshot 2023-04-09 200321](https://user-images.githubusercontent.com/115066186/230774271-35092c13-d144-4d50-b318-a7482c0fffc6.png)
![ROwxRiCm34LtVOM0ZWRy1HrSsqE1BaLReBDW4J4HYGpqW8Sa_nxPbXzvREIvkjIfV50kH6j4PvJtyWSyQg0Epg9ecPqe_f4q3-Aj1ksORHfKwEVf2qFN0ubhBdzoz6EnKKv-AtTSWpgYqKY7lFwcqS3qEfC_7cY_VvoK2nOevBtX966HCDhb1bXi8QWaeEV](https://user-images.githubusercontent.com/115066186/230774263-9df7ea37-812b-4ecc-903c-a31f9feea90f.png)

## 2. [แผนภาพตามแนวคิด Association abstraction](Week04-lab-part-02.md)


