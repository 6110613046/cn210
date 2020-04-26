# เนื้อหาต่างๆในราบวิชา CN210
### หน้าเว็ปนี้ได้รวนเนื้อหาคลิปวีดีโอที่เกี่ยวข้องกับการเรียนการสอนในวิชา CN210
### เนื้อเริ่มต้นโดยสังเขบ
![image](http://don-jai.com/wp-content/uploads/2009/11/MIPS_instruction_set.jpg)

– MIP มี instruction อยู่ 3 แบบ

– ในแต่ละฟิลด์ มีความหมายดังต่อไปนี้

op: พื้นฐานการทำงานของคำสั่ง ซึ่งเรียกว่า opcode

rs: รีจีสเตอร์ ตัวแปรกระทำ ตัวแรก (s = source)

rt: รีจีสเตอร์ ตัวแปรกระทำ ตัวสอง (t = target)

rd: รีจีสเตอร์ ที่เก็บผลลัพธ์ (d = destination)

shamt: ค่าของการเลื่อนตำแหน่ง

funct: ฟังก์ชั่น เป็นฟิลด์ที่กำหนดการกระทำย่อยๆ ที่อธิบายเสริมกับพื้นฐานการทำงานของคำสั่ง หรือเรียกว่า function code

<br>**คลิปที่ 1**
*computer architecture j-type mipsc*

อธิบายคำสั่ง jump ใน cpu MIPS

J-type (jump type)

– เป็นคำสั่งที่มี imm มากสุดคือ 26 bit

– โดย 26 bit นี้อยู่ในโหมด word addressing, ถ้าอยู่ในรูปแบบ byte addressing จะได้ 28 bit

– จากการ Instrument code (ใส่โค้ดเข้าไปเพื่อดูว่าการเปลี่ยนของ program counter เป็นอย่างไร)ของ MIPS พบว่าการ jump ไม่เคยเกิน 28 bit ซักที ดังนั้น MIPS ก็เลย implement คำสั่ง J-Type ขึ้นมา

– ถ้า jump เกิน 28 bit ก็ให้ใช้คำสั่งอื่นเช่น jump register

<br>[CLIP1](https://youtu.be/-NUaUiUUi6Q)

<br>**คลิปที่ 2**
*CPU MIPS Processing*
<br>[CLIP2](https://youtu.be/hFsSilVuIrM)

<br>**คลิปที่ 3**
*Single-cycle VS Multi-cycle CPU MIPS*
<br>[CLIP3](https://youtu.be/G5QxbVlIw1o)

<br>**คลิปที่ 4**
*การทำงานของlw ใน multi cycle*
<br>[CLIP4](https://youtu.be/6N-0znIz0XU)

<br>**คลิปที่ 5**
*การทำงานของbeqในMulti cycle*
<br>[CLIP5](https://youtu.be/CurPkd1jGK4)

<br>**คลิปที่ 6**
*R Format State machine step*
<br>[CLIP6](https://youtu.be/pd521LRO-JM)

<br>**คลิปที่ 7**
**
<br>[CLIP7]()
