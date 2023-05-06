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

![image](https://user-images.githubusercontent.com/115066431/236639824-054fd3c5-8e44-4fc9-92b0-3fea08b00b6b.png)
![image](https://user-images.githubusercontent.com/115066431/236639866-c08a740d-5fc6-460a-85b3-0a18392db738.png)






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
![image](https://user-images.githubusercontent.com/115066431/236639838-bdae28c3-a3ed-4971-bd3d-3522dad53537.png)



![image](https://user-images.githubusercontent.com/115066431/236639664-4a6cf8c4-435b-435f-b081-8c6b412634b2.png)





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
![image](https://user-images.githubusercontent.com/115066431/236639553-3cba9978-0c7e-4158-afba-78a14da09419.png)
![image](https://user-images.githubusercontent.com/115066431/236639687-d122bc0b-a125-4837-8259-4b0aebaee5f2.png)



### จบการทดลองและแบบฝึกหัด
