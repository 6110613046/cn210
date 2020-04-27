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

#### ความต่างระหว่าง single-clock-cycle กับ multi-clock-cycle

##### ลักษณะของ Single Cycle 
        
     -  มี ALU 3 ตัว   
        
     -  มี Memory 2 ตัว 
       
     -  1 คำสั่ง = 1 Cycle  
        
##### ลักษณะของ Multi Cycle มีดังนี้

     -  มี ALU เพียงตัวเดียว
        
     -  มี Memory เพียงตัวเดียว
       
     -  มีการพักข้อมูลที่ตำแหน่ง a และ b ในรูป
        
     -  ใช้เวลาแต่ละคำสั่งไม่เท่ากัน
        
     -  มี ALUout ที่เก็บค่าหลังจากคำนวณ

<br>[CLIP3](https://youtu.be/G5QxbVlIw1o)

<br>**คลิปที่ 4**

#### การทำงานของlw ใน multi cycle

  ##### คำสั่ง lw ใน Multi Cycle นั้นมีทั้งหมด 5 ขั้นตอน
        
        1.อ่านคำสั่งจาก Memory มาเก็บใน IR (Instruction Register) และนำ PC = PC + 4 พร้อมๆกัน
        
        2.นำ ค่าจาก $rs และ $rt ไปเก็บไว้ที่ A,B ตามลำดับ นำค่า offset มาแปลงเป็น 32 บิท
          แล้วนำไปที่ ALU เพื่อบวกกับ PC แล้วนำไปเก็บที่ ALUout (A = Reg[IR[25-21]]) (B = Reg[IR[20-16]])
       
        3.นำค่า จาก A เข้ามาบวกกับ offset และนำค่าไปไว้ที่ ALUout (ALUOut = A + sign-extend(IR[15-0])
        
        4.ค่าที่ได้จาก ALUout คือ ค่าของ Address ของ Memory ที่จะถูกอ่านค่าออกมา (MDR = Memory[ALUout])
        
        5.นำค่าที่อ่านมาจาก Memory ไปเก็บไว้ใน $rt (Reg[IR[20-16]] = MDR)

<br>[CLIP4](https://youtu.be/6N-0znIz0XU)

<br>**คลิปที่ 5**

#### การทำงานของ beq ในmulti-clock-cycle
        
 ##### beq (branch on equal) เป็นคำสั่งประเภท I-Format ซึ่งคำสั่งนี้มีหน้าที่ JUMP โดยจะ JUMP อย่างมีเงื่อนไข 
        
 #####  คือการดูว่าข้อมูลที่ $rs และ $rt เท่ากันหรือไม่ หากเท่ากันให้ JUMP ไปยังตำแหน่ง Address ต่อไป 
        
 #####  มี 3 ขั้นตอน
        
        1.อ่านคำสั่งจาก Memory มาเก็บใน IR (Instruction Register) และนำ PC = PC + 4 พร้อมๆกัน
        
        2.นำค่า $rs และ $rt ไปเก็บไว้ที่ A,B ตามลำดับ (A = Reg[IR[25-21]]) (B = Reg[IR[20-16]])
       
        3.นำค่าจาก A และ B มาเปรียบเทียบกัน หากเท่ากันจะเก็บผลลัพธ์ที่ได้ไว้ใน ALUout แล้ว JUMP ไปยัง Address ต่อไปหากไม่เท่ากันจะข้ามไปทำคำสั่งถัดไปทันที     

<br>[CLIP5](https://youtu.be/CurPkd1jGK4)

<br>**คลิปที่ 6**

อธิบายสัญญาณที่ใช้ควบคุมใน R-format

ประกอบด้วย 4 ขั้นตอน

  1.      MemRead = 1 คือ ทำการอ่านค่าจาก Memory
          IorD = 1 คือ เช็คว่า PC นั้นชี้ไปที่ Address ใดใน Memory
          IRWrite = 1 คือ นำค่าจาก Address Memory ที่ถูกชี้ ไปเก็บไว้ใน IR
          ALUSrcA = 0 คือ Mux เลือกค่าจาก 0 ซึ่งคือ PC ค่าที่ถูกเขียนใน IR จะมี ALUSrcA ทำการควบคุม
          ALUSrcB = 1 คือ Mux เลือกค่าจาก 1 ซึ่งคือ 4 ค่าที่ถูกเขียนใน IR จะมี ALUSrcB ทำการควบคุม
          ALUOP = ADD คือ การนำค่า PC มาบวกกับ 4
          PCWrite = 1, PCSource = 1 นำผลลัพธ์การคำนวณเขียนทับที่ PC = PC + 4
              
  2.      ALUSrcA = 0 คือ Mux เลือกค่าจาก 0 ซึ่งคือ PC
          ALUSrcB = 3 คือ Mux เลือกค่าจาก 3 ซึ่งคือ Offset
          ALUop = 0 คือ ALUop จะทำการควบคุมคำสั่ง ADD
        
  3.      ALUSrcA = 1 คือ Mux เลือกค่าจาก 1 ซึ่งคือ $rs
          ALUSrcB = 0 คือ Mux เลือกค่าจาก 0 ซึ่งคือ $rt
          ALUop = 2 คือ ALUop จะทำการควบคุมคำสั่งให้เป็นไปตามคำสั่งใน IR
 
  4.      RegWrite = 1 คือ นำค่าจาก ALUout มาเขียนใน $rd
          MemtoReg = 0 คือ Mux เลือกค่าจาก 0 ซึ่งคือ ALUout
          RegDst = 1 คือ Mux เลือกค่าจาก 1 ซึ่งคือ $rd

<br>[CLIP6](https://youtu.be/pd521LRO-JM)

<br>**คลิปที่ 7**

#### กล่าวถึงการทำงานของ Pipelining

<br>[CLIP7](https://youtu.be/l0J13kpTUMA)
