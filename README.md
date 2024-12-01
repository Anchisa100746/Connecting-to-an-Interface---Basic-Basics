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



หลังการติดตั้ง

1.เปิดโปรแกรม Arduino IDE ขึ้นมา

2.ตรวจสอบว่าได้เลือกบอร์ดที่ถูกต้อง (เช่น Arduino Uno, ESP32, เป็นต้น) โดยไปที่ Tools > Board และเลือกบอร์ดที่ใช้

3.เลือกพอร์ตที่เชื่อมต่อกับบอร์ดใน Tools > Port

![image](https://github.com/user-attachments/assets/533ca3ce-eccb-4495-8077-fbc00aeb0c4d)








































































