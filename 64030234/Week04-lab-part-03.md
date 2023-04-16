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
![Lab5](./Images/Diagram1.1.png)

![Lab5.1](./Images/Diagram1.png)

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
![Lab6](./Images/Diagram1.2.png)

![Lab6.1](./Images/Diagram2.png)


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
![Lab7](./Images/Diagram1.3.png)

![Lab7.1](./Images/Diagram3.png)

### จบการทดลองและแบบฝึกหัด