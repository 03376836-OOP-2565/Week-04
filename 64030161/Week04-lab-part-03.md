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

![image](https://user-images.githubusercontent.com/115066261/217012098-af5bb3ef-71cc-4730-862d-9f2407aa43d2.png)

<img width="903" alt="Screenshot 2566-02-06 at 22 24 49" src="https://user-images.githubusercontent.com/115066261/217012201-ea5788b7-2eff-4d00-ada7-764dc08af35d.png">

```
ตรงตามที่คิด
```

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

![image](https://user-images.githubusercontent.com/115066261/217014327-9752bfbf-10e5-4e80-970d-c388bec693a2.png)


<img width="1242" alt="Screenshot 2566-02-06 at 22 33 17" src="https://user-images.githubusercontent.com/115066261/217014290-c58a7782-48cf-44b5-ae51-71831d81b193.png">

```
ตรงตามที่คิด
```

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

![image](https://user-images.githubusercontent.com/115066261/217019079-3fd760cf-9f86-4f2c-bd3c-a6efb31c3f68.png)

<img width="1239" alt="Screenshot 2566-02-06 at 22 52 59" src="https://user-images.githubusercontent.com/115066261/217019237-963e1145-a4b2-402f-811c-6863399ab3df.png">

```
ตรงตามที่คิด
```
### จบการทดลองและแบบฝึกหัด
