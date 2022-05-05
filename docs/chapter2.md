## บทที่ 2 พื้นฐานระบบสื่อสาร 
### Lora Physical layer

   เริ่มต้นการลงมือใช้งาน ESP8266 หรือ NodeMCU จากการลงโปรแกรม

Arduino IDE คือ ซอฟแวร์ที่รวบรวมเครื่องมือต่างๆ (การติอต่อกับ ฮาร์ดแวร์ การ Compile โปรแกรม Editor ที่ใช้ในการเขียน Skecth การทดสอบการทำงานของโปรแกรมที่พัฒนาขึ้นบนบอร์ด) ซื่งจำเป็นที่ต้องใช้ในการพัฒนาระบบไมโครคอนโทรลเลอร์
สามารถดาว์นโหลดโปรแกรม Arduino IDE [ได้ที่](https://www.arduino.cc/en/software) โดยตุณสามารถเลือกใช้ตาม OS ของคุณ

<p align="center">
<img src="https://files.seeedstudio.com/wiki/Seeeduino_Stalker_V3_1/images/Download_IDE.png" alt="alt text" title="IDE Download" width="500"/>
</p>

### การติดตั้งไดรเวอร์ของพอร์ต USB
- บอร์ด Arduino ติดต่อกับเครื่องพีซีผ่านเคเบิ่ลที่ใช้หัว USB รุ่นต่างๆ ซึ่งไดรเวอร์ของหัว USB ที่ต้องติดตั้งนั้น ขึ้นกับชนิดของ Chip ที่ใช้บนบอร์ด Arduino ของคุณ หมายเหตุ: โดยปกติแล้วชนิดของชิบ USB จะถูกระบุไว้บนด้านหลังของตัวบอร์ด
- ดาวน์โหลด ไดรเวอร์ของ USB รุ่น CP2102. หมายเหตุ: โปรดเลือกตาม OS ที่คุณใช้
- หลังจากติดตั้งไดรเวอร์สำเร็จแล้ว ให้ต่อบอร์ด Arduino โดยใช้สายแลหัวต่อ USB เข้ากับเครื่องคอมพิวเตอร์
- สำหรับผู้ใช้ระบบปฏิบัติการ Windows คุณสามารถดูพอร์ตที่ติดตั้งได้จาก 'My Computer' -> Properties -> Hardware -> Device Management จะเห็น 'COM' และตัวเลขแสดงพอร์ต
- สำหรับผู้ใช้ Mac OS คุณสามารถดูพอร์ตที่ติดตั้งได้จาก  ที่มุมบนด้านซ้าย และเลือก About this Mac -> System Report... -> USB. จะเห็น CP2102 USB Driver
- กรณีที่ยังไม่ได้ติดตั้งไดรเวอร์ หรือ ติดตั้งไม่ถูกต้องกับ Chip ที่ใช้ จะเห็น "unknown device" ใน device manager ให้ติดตั้งไดรเวอร์ใหม่

### เริ่มต้นใช้งาน Arduino IDE
1. ปิดโปรแกรม Arduino IDE บนเครื่อง PC ของคุณ
2. คลิ๊กเลือก Tools -> Board เพื่อเลือกชนิดของบอร์ด และเลือก Arduino/Generic ESP8266 เป็นบอร์ดที่คุณใช้
3. คลิ๊ก Tools -> Port เพื่อเลือก Port ที่ถูกต้อง (เลือกให้ตรงกับ Port ที่แสดงไว้ในขั้นตอนก่อนหน้า). ในตัวอย่างนี้เลือก COM6
4. สร้างไฟล์ใหม่และใช้ชื่อ HelloWorld.ino จากนั้น copy โปรแกรมไปไว้ในไฟล์ที่สร้าง:

<font size=5;font color=#314B9F >การต่อวงจร</font>

- **Module connection**
    - ต่อสาย USB เข้ากับบอร์ดและช่อง USB ของเครื่องคอมพิเตอร์
    
<font size=5;font color=#314B9F >โค้ดที่ใช้ทดสอบ</font>

- เปิด Arduino IDE.
- Copy โค้ดด้านล่าง และกด Verify เพื่อตรวจสอบความถูกต้องของ Syntax และความผิดพลาดอื่นๆ จากนั้น Upload โค้ด
  
```Cpp linenums="1"
void setup() {
Serial.begin(9600); // initializes the serial port with a baud rate of 9600
}
void loop() {
Serial.println("hello, world"); // prints a string to a serial port
delay(1000); //delay of 1 second
}
```