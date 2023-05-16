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
![Screenshot 2023-04-09 202417](https://user-images.githubusercontent.com/115066186/230776443-d94cb4a5-866c-4458-9bbe-6a3657df7876.png)
![Screenshot 2023-04-09 202609](https://user-images.githubusercontent.com/115066186/230776445-b61aee9d-84fd-45e0-be8e-e896aef2fdb7.png)

ตรงตามที่คิด

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
![Screenshot 2023-04-09 203151](https://user-images.githubusercontent.com/115066186/230776462-1f123b31-8423-4db6-a1ae-3ed70e789809.png)
![Screenshot 2023-04-09 203213](https://user-images.githubusercontent.com/115066186/230776467-d74d5027-9769-4877-a8e7-8bdaf44bfd66.png)

เป็นไปตามที่คิด

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
![Screenshot 2023-04-09 204657](https://user-images.githubusercontent.com/115066186/230776481-c13e7647-bf54-4299-b7e6-a9d561ec7d1b.png)
![Screenshot 2023-04-09 204719](https://user-images.githubusercontent.com/115066186/230776487-af85dfad-5bfb-4290-bb25-53d5e8cd53d9.png)

เป็นไปตามที่คิด

### จบการทดลองและแบบฝึกหัด
