# Connecting-to-an-Interface---Basic-Basics
ใบงานการทดลอง  เรื่อง การอินเตอร์เฟสกับเอาต์พุต -  อินพุตพื้นฐาน

หัวข้อย่อย: การอ่านค่าจาก Sensor HC-SR04 

คำชี้แจง

        1.ให้นักเรียนทำการเชื่อมต่อวงจรเซ็นเซอร์ HC-SR04 กับบอร์ด ESP32 ตามภาพที่กำหนด
        2. เขียนโปรแกรมสำหรับการอ่านค่าระยะทางจากเซ็นเซอร์ HC-SR04
        3.ทำการทดสอบและแสดงผลลัพธ์ของโปรแกรมให้ถูกต้อง
        4.จดบันทึกค่าระยะทางที่ได้ และสรุปผลการทดลอง
        
ขั้นตอนการเตรียมอุปกรณ์

         1.บอร์ด ESP32 
         2.สายไฟ หรือ สายจั้ม
         3.เซ็นเซอร์ HC-SR04
         4.แหล่งจ่ายไฟ หรือต่อเชื่อมกับ USB
         5.โปรแกรม Arduino IDE
         
ขั้นตอนการทดลอง

1.	ให้นักเรียนต่อเชื่อมกับอุปกรณ์ตามภาพ ดังนี้


![image](https://github.com/user-attachments/assets/332bffac-0215-447c-a34f-54e6b264faf9)


         1.สาย VCC ของเซ็นเซอร์ต่อเข้ากับ แหล่งจ่ายไฟ 5V บนบอร์ด     
         2.สาย GND ของเซ็นเซอร์ต่อเข้ากับ GND บนบอร์ด
         3.สาย TRIG ของเซ็นเซอร์ต่อเข้ากับ GPIO 16                           
         4.สาย Echo ของเซ็นเซอร์ต่อเข้ากับ GPIO 05                             


2.ให้นักเรียนดาวน์โหลด หรือเปิด โปรแกรม  Arduino IDE

   ลิ้งค์ดาวน์โหล  https://www.arduino.cc/en/software


![image](https://github.com/user-attachments/assets/c777cbb3-3680-4bf5-837e-a6f647c02110)



### หลังการติดตั้ง

1.เปิดโปรแกรม Arduino IDE ขึ้นมา

2.ตรวจสอบว่าได้เลือกบอร์ดที่ถูกต้อง (เช่น Arduino Uno, ESP32, เป็นต้น) โดยไปที่ Tools > Board และเลือกบอร์ดที่ใช้

3.เลือกพอร์ตที่เชื่อมต่อกับบอร์ดใน Tools > Port

![image](https://github.com/user-attachments/assets/67a91061-51a7-400c-b2d0-c8f6ab3aee91)


4.กด File และกด  New Sketch

![image](https://github.com/user-attachments/assets/3c0017c7-c022-455e-8f35-9d7d233d1d89)

จะขึ้นหน้าแบบนี้ขึ้นมา

![image](https://github.com/user-attachments/assets/63caad41-9af6-46fa-bcff-43f39b8ccf3e)


5.กด ตรง ลูกศร พิมย์คำว่า ESP 32 กด INSTALL สีเขียว

![image](https://github.com/user-attachments/assets/bf53c575-6024-4100-a3d2-49bb7d94bb05)

![image](https://github.com/user-attachments/assets/3c76241e-0ed2-4b9d-8839-f806955f7a75)

6.ถ้ายังไม่ได้ติดตั้ง  การติดตั้ง Driver CH340 สำหรับ Arduino SMD ให้ติดตั้งก่อน โดยไปหน้าเว็บนี้

https://www.ab.in.th/article/   หรือพิมคำว่า  ดาวน์โหลดไดรเวอร์ CH340

7.จะขึ้นหน้าตาแบบนี้ ต่อไปให้กดคลิกขวา ตรงโฟรเดอร์ และกดแตกไฟล์

![image](https://github.com/user-attachments/assets/5af456a6-6538-4b02-b1aa-e9955907d7fe)

8.เพิ่มบอร์ด ESP ใน Arduino IDE

    1.เปิด Arduino IDE และไปที่ File > Preferences (หรือ Arduino > Preferences บน macOS)
    2.ในช่อง Additional Board Manager URLs ให้ใส่ URL ต่อไปนี้:
       สำหรับ ESP32:

          https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
          
     3.คลิก OK

    4.ไปที่ Tools > Board > Board Manager แล้วค้นหา ESP32 
    5. คลิก Install เพื่อติดตั้งแพ็กเกจสำหรับบอร์ดที่ต้องการใช้งาน

![image](https://github.com/user-attachments/assets/5866c15e-d57b-4250-bdd7-65a2f397c391)


9. ตั้งค่าบอร์ด

            1.เชื่อมต่อบอร์ด ESP กับคอมพิวเตอร์ผ่านสาย USB
            2.ไปที่ Tools > Board และเลือกบอร์ดที่ตรงกับรุ่นของคุณ (เช่น ESP32 Dev Module หรือ NodeMCU 1.0)
            3.เลือกพอร์ต (Port) ที่บอร์ดเชื่อมต่อ
                 oไปที่ Tools > Port แล้วเลือก COM พอร์ตที่แสดง (บน Windows)

![image](https://github.com/user-attachments/assets/16ca734d-db2e-4053-b0af-cccca79df540)


10. เขียนโปรแกรม
    
        โปรแกรมสำหรับวัดระยะห่างจากวัตถุ ด้วย Sensor HC-SR04 บนบอร์ด ESP32

![image](https://github.com/user-attachments/assets/88d97761-b334-4767-95a3-f81198e4f1d4)

``` cpp
#define TRIG_PIN 4
#define ECHO_PIN 5

void setup() {
  Serial.begin(115200);
  pinMode(TRIG_PIN, OUTPUT);
  pinMode(ECHO_PIN, INPUT);
}

void loop() {
  digitalWrite(TRIG_PIN, LOW);
  delayMicroseconds(2);
  digitalWrite(TRIG_PIN, HIGH);
  delayMicroseconds(10);
  digitalWrite(TRIG_PIN, LOW);

  long duration = pulseIn(ECHO_PIN, HIGH);
  float distance = (duration * 0.034) / 2;

  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");
  delay(1000);
}
``` 






































