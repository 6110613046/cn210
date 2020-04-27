# เนื้อหาต่างๆในราบวิชา CN210
### หน้าเว็ปนี้ได้รวนเนื้อหาคลิปวีดีโอที่เกี่ยวข้องกับการเรียนการสอนในวิชา CN210
### เนื้อเริ่มต้นโดยสังเขบ

ส่วนประกอบของคอมพิวเตอร์ 

       1.หน่วยประมวลผลกลาง หรือ CPU(Central Processing Unit)

       2.main memory

       3.Input/Output

ส่วนประกอบในส่วนของ CPU

       1.ALU(Artimetric and logic unit) ใช้ในการคำนวณและหาตรรกะทางคณิตศาสตร์

       2.Register

       3.Control Unit


![image](http://don-jai.com/wp-content/uploads/2009/11/MIPS_instruction_set.jpg)

– MIP มี instruction อยู่ 3 แบบ

       I-Type (immediate type)
       
       R-Type (Register)
       
       J-type (jump type)

– ในแต่ละฟิลด์ มีความหมายดังต่อไปนี้

      op: พื้นฐานการทำงานของคำสั่ง ซึ่งเรียกว่า opcode

      rs: รีจีสเตอร์ ตัวแปรกระทำ ตัวแรก (s = source)

      rt: รีจีสเตอร์ ตัวแปรกระทำ ตัวสอง (t = target)

      rd: รีจีสเตอร์ ที่เก็บผลลัพธ์ (d = destination)

      shamt: ค่าของการเลื่อนตำแหน่ง

      funct: ฟังก์ชั่น เป็นฟิลด์ที่กำหนดการกระทำย่อยๆ ที่อธิบายเสริมกับพื้นฐานการทำงานของคำสั่ง หรือเรียกว่า function code

อธิบายคำสั่ง jump ใน cpu MIPS

#### J-type (jump type)

  |B31-26  |   B25- 0   |
   ------- | ---------- |
  |opcode  |   target   |

    – เป็นคำสั่งที่มี imm มากสุดคือ 26 bit

    – โดย 26 bit นี้อยู่ในโหมด word addressing, ถ้าอยู่ในรูปแบบ byte addressing จะได้ 28 bit

    – จากการ Instrument code (ใส่โค้ดเข้าไปเพื่อดูว่าการเปลี่ยนของ program counter เป็นอย่างไร)ของ MIPS พบว่าการ jump ไม่เคยเกิน 28 bit ซักที ดังนั้น MIPS ก็  เลย implement คำสั่ง J-Type ขึ้นมา

    – ถ้า jump เกิน 28 bit ก็ให้ใช้คำสั่งอื่นเช่น jump register
  
#### I-Type (immediate type) 

   |B31-26 |   B25-21   |	 B20-16 |  B15-0   |
   ------- | ---------- | ---------- | ------- |
   |opcode | register s | register t | address |
  
    – มีรีจิสเตอร์อยู่ 2 ตัวคือ rs,rt แล้วตามด้วย immediate ซึ่งต้องเป็น 2’s complement เท่านั้น

#### R-Type (Register
   |B31-26 |   B25-21   |   B20-16   |  B15-11    |   B10-6      |  B5-0   | 
   ------- | ---------- | ---------- | ---------- | ------------ | ------- |
   |opcode | register s | register t | register d | shift amount | funct   |
  
    – ตัวอย่างเช่น add $3 $4 $5
    
    - rd คือตัวระบุ destination
    
    – ดังนั้นถ้าเปรียบเทียบระหว่าง R-type กับ I-Type
  
    – op บอกว่าคำสั่งหลักเป็นคำสั่งอะไร โดย การเปลี่ยนแปลงว่าจะทำอะไร ของคำสั่งจะอยู่ใน function
  
    – function คือ การเปลี่ยนแปลงว่าจะทำอะไร ของคำสั่งหลัก


<br>**คลิปที่ 1**

กล่าวถึงการทำงานของ

#### j-type 

*computer architecture j-type mipsc*

<br>[CLIP1](https://youtu.be/-NUaUiUUi6Q)

<br>**คลิปที่ 2**

กล่าวถึง การพูดภาษาคอมไปเป็นภาษาคน

#### code

        class Test { 

                public static void main(String[] args){

                         int a = 10;
    
                         int b = 20;
    
                         int c = a+b;
                 }
        }

#### Machine Language 

     00000000:           08400000        //jumpไปที่ address  01000000 
    
     00000004:           1A000000        //data
    
     ...

     01000000:           8C090004        //lw $9,$0(4) ดึงข้อมูลจากaddressของregisterที่0 + 4 นำไปเก็บไว้ที่registerที่9
    
     01000004:           8D210000       //lw $1,$9(0) ดึงข้อมูลจากaddressของregisterที่9 + 0 นำไปเก็บไว้ที่registerที่1

     01000008:           8D220004       //lw $2,$9(4)  ดึงข้อมูลจากaddressของregisterที่9 + 4 นำไปเก็บไว้ที่registerที่2

     0100000C:           00221820        //add $3,$1,$2 register3 = register1 + register2

     01000010:           AD230008        //sw $9,$0(4)  นำข้อมูลจากaddressของregisterที่9 นำไปเก็บไว้ที่registerที่0 + 4 

     .....

     1A000000:           0000000A        //a = 10

     1A000004:           00000014        //b = 20

     1A000008:           0000001E        //c = 30
     
    
**CPU MIPS Processing**

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
