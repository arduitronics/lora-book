# ESP8266 Barebone with lora
## การใช้งาน ESP8266 Low power
รายละเอียดต่อไปนี้เป็นการใช้งาน ESP8266 แบบ Low power  ซึ่งเป็นการใช้เฉพาะ Chip ESP-8266 ไม่ได้ใช้งานแบบ NodeMCU โดย [Arduitronics.com](https://www.arduitronics.com) 

<p align="center">
<img src="https://github.com/arduitronics/ESP-kit1/blob/main/docs/img/esp12f.jpg?raw=true" alt="alt text" title="ESP12F" width="350"/>
</p>

เป้าหมายเป็นการศึกษาการตอบสนองการใช้งานรับส่งค่าที่อ่านได้จาก Node ต่างๆ โดยกำหนดให้จ่ายแรงดันจากแบตเตอรี่แบบ Lithium 18650 เพียงก้อนเดียว (2200 mAh) ให้ได้นานที่สุด (มากกว่า 3 เดือน) ทดสอบโดยการใช้ ESP8266 อ่านค่าแรงดันไฟฟ้าของแบตเตอรี่ที่จ่ายแรงดันให้กับ ESP8266 ด้วย Pin A0 

ขั้นตอนการทำงานในการทดสอบการใช้พลังงานของบอร์ด ESP8266 ที่จะทดสอบมีดังนี้

1. เชื่อมต่อกับระบบ WiFi Work ในบริเวณใกล้เคียง โดยเลือก SSID ที่มีสัญญาแรงที่สุด
2. log in เข้าระบบ Netpie 2015
3. อ่านค่าจาก Analog input A0
4. ส่งค่าที่อ่านได้แสดงบน netpie

เพื่อการสังเกตการใช้พลังงานของ ESP8266  MCP1700 (Low power voltage regulator) และองค์ประกอบอื่นๆ ในการอ่านค่า ทำได้โดยการวัดกระแสที่ผ่านเข้าในแต่ละองค์ประกอบของวงจร 

## การต่อวงจรที่ใช้ทดสอบ
  ในการทดสอบนี้ หลังจากอ่านค่าจาก Analog channel A0 และส่งค่าไปที่ Netpie แล้ว  EPS8266 จะเข้าสู่ Deep sleep mode เพื่อประหยัดพลังงาน  อย่างไรก็ตามถึงแม้จะอยู่ใน Deep sleep แต่ Internal Clock ยังสามารถใช้งานได้ และสามารถใช้เป็น Interupt เพื่อปลุกให้ตัว ESP8266 ตื่นขึ้นมาทำงานได้
  <p align="center">
  <iframe width="560" height="315" src="https://www.youtube.com/embed/NgPwPKXCLFY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  </p>

## Voltage Divider
 การวัดค่าแรงดันของแบตเตอรี่ทำได้โดยการใช้วงจร Voltage divider  อย่างไรก็ตามหากใช้ตัวต้านทานมาประกอบเป็น Voltage divider โดยตรงนั้น จะทำให้มีกระแสไหลผ่านตัวต้านทานตลอดเวลา ส่งผลต่ออายุการทำงานของวงจร ดังนั้นจึงต้องการวัดค่าแรงดันเฉพาะช่วงเวลาที่ต้องการเท่านั้น (เวลาที่ ESP8266 ตื่นมาทำงาน) ซึ่งเป็นช่วงเวลาสั้นๆ 

<p align="center">
<img src="https://github.com/arduitronics/ESP-kit1/blob/main/docs/img/voltagedivider.jpg?raw=true" alt="alt text" title="ESP12F" width="500"/>
</p>
[5 Voltage divider circuits that go beyond dividing](https://www.baldengineer.com/5-voltage-divider-circuits.html "Voltage divider")


## Deep Sleep และ Wake up 
  การทำให้ ESP8266 เข้าสู้โหมด Deep sleep ทำโดยใช้คำสั่ง 

 `ESP.deepSleep(sleepTimeS * 1000000); `


## Sketch ที่ใช้ทดสอบ
<script src="https://gist.github.com/arduitronics/307b8a52f746252126d8d213875d65df.js"></script>