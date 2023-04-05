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

![ภาพ](https://user-images.githubusercontent.com/115066278/230163507-53552407-4f47-47c5-85ae-507fde94c662.png)


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

![ภาพ](https://user-images.githubusercontent.com/115066278/230163532-a2920744-31b5-4afe-ab34-4288e4704e45.png)



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


![ภาพ](https://user-images.githubusercontent.com/115066278/230163567-e9c5286c-4394-430d-b387-6efb94038cb5.png)


### จบการทดลองและแบบฝึกหัด
