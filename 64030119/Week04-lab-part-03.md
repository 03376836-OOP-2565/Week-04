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
![image](https://user-images.githubusercontent.com/115066285/232202665-a4fb00cf-dcd0-4552-8f3a-00884dff2958.png)
![image](https://user-images.githubusercontent.com/115066285/232202723-49b9183f-a0c7-496e-8477-290746fcd1d0.png)
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
![image](https://user-images.githubusercontent.com/115066285/232202674-842f0c81-f716-4da4-8ffc-cc985b01838b.png)
![image](https://user-images.githubusercontent.com/115066285/232202756-79f5190f-b1ce-4f10-a635-4912123a3ad6.png)
ตรงตามที่คิด
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
![image](https://user-images.githubusercontent.com/115066285/232201054-12e4ddd7-3b16-49f6-8eb2-6385d7c11e5c.png)
![image](https://user-images.githubusercontent.com/115066285/232201085-e4d00869-3135-4e88-8982-78742d0a195e.png)
ตรงตามที่คิด


### จบการทดลองและแบบฝึกหัด
