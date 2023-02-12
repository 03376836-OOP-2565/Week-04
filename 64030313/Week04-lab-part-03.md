# การทดลอง วาดไดอะแกรมด้วย plantUML (2)
## การวาดไดอะแกรมที่มีองค์ประกอบมากขึ้น

ให้นักศึกษาพิจารณาวาด uml diagram ของ code ต่อไปนี้ในกระดาษ โดยยังไม่ต้องใช้ plantuml จากนั้นให้ไปวาดใน  plantuml แล้วเปรียบเทียบผลที่ได้ว่าตรงตามที่คิดหรือไม่


1. 

``` plantuml
@startuml
"Football team" "1..1" *-- "12..20" "Player"
"Football team" "1..1" *-- "1..2" "Coach"
"Coach" - "Player": > teach
@enduml
```
## รูปวาด
![1](https://user-images.githubusercontent.com/115037574/218331007-b6dc4975-e353-462b-9c2e-229585e61f11.jpg)
## planuml
![image](https://user-images.githubusercontent.com/115037574/217548156-21ee8ed1-5d12-4777-9cdc-757133ffcb4e.png)

2. 

``` plantuml
@startuml
class Student
{
  - name
  - ID
  - GPA
  + enrollSubject()
  + takeExamination()
}

class Subject
{
  - name
  - capacity
  - studytime
  + enrollStudent()
  + exam()
}

class Professor
{
  - name
  - emailAddress
  - instructs()
}

Student "10..40" - "0..1" Subject : > enrolled in
Subject "1" - "1..3 "Professor : < instructs
@enduml

```
## รูปวาด
![2](https://user-images.githubusercontent.com/115037574/218331050-eb35b774-4408-4602-a8e3-ffe4d3b34220.jpg)
## planuml
![image](https://user-images.githubusercontent.com/115037574/217548321-e4054b4b-7404-4ca2-8205-786d17b04ec9.png)

3. 
``` plantuml
@startuml
class Clock
{
 - time
 + getTime()
 + incrementTime()
}

class Display
{
 - time
 + initTime()
 + setTime()
 + displayTime()
}

class HistoryCall
{
 - count
 + call()
 + answer()
} 

class Call
{
 - callDuration
 + getDuration()
} 

class OutgoingCall
{
  - number
  + Dial()
}

class IncomingCall
{
  - number
  + Answer()
}

MobilePhone "1" *-- "1" Clock
MobilePhone "1" *-- "1" Display
MobilePhone "1" *- "1" HistoryCall
HistoryCall "1" *-- "n" Call
Call <|-- IncomingCall
Call <|-- OutgoingCall
OutgoingCall "1" -- "1..12" DialPad : > use
IncomingCall "1" -- "1..2" AnswerButton : > use
DialPad -|> Keypad 
Keypad <|- AnswerButton
@enduml
```
## รูปวาด
![3](https://user-images.githubusercontent.com/115037574/218331057-fc08ef3c-191d-4351-8c94-80752cb47c84.jpg)
## planuml
![image](https://user-images.githubusercontent.com/115037574/217548423-6b6ed723-5b47-43db-83e4-20d2c88050a5.png)

### จบการทดลองและแบบฝึกหัด
