# การทดลองที่ 2 เรื่อง การเขียนโปรแกรมค้นหาไวไฟ
## วัตถุประสงค์
1.เพื่อศึกษาmicrocontroller ในการใช้ค้นหา wifi ที่อยู่รอบๆ
2.เพื่อศึกษาเกี่ยวกับการ run microcontroller
## อุปกรณ์ที่ใช้
1. คอมพิวเตอร์
2. microcontroller ESP01
3. อุปกรณ์ต่อ USB-Serial
4. เสาไวไฟ
## ศึกษาข้อมูลเบื้องต้น
1. run example 2 https://youtu.be/yBjab0UNuB8
2. code 02_scan-wifi https://github.com/choompol-boonmee/lab63b/blob/master/examples/02_Scan-Wifi/platformio.ini
## วิธีทำการทดลอง
1. เชื่อมต่อ microcontroller เข้ากับคอมพิวเตอร์ด้วยการต่อ USB ไปยัง Serial
2. เปิด cmd ซึ่งจากตัวอย่างอยู้ในโฟล์เดอร์ ใช้คำสั่ง cd pattani
3. ใช้คำสั่ง cd 02_scan-wifi
4. ใช้คำสั่ง 1s ตามด้วยค่ำสั่ง vi src/main.cpp เพื่อเตรียมอัพโหลดโปรแกรมใน microcontroller
![alt text](https://cdn.discordapp.com/attachments/823124660014940180/824288952159830066/Screenshot_2021-03-24_212915.jpg)
4. ใช้คำสั่ง pio run -t upload เพื่ออัพโหลดโปรแกรมเข้า microcontroller
5. ใช้คำสั่ง pio device monitor เพื่อเตรียมสแกนหา wifi
![alt text](https://cdn.discordapp.com/attachments/663373978848591875/824227472353787924/112263855-8c37f480-8ca2-11eb-863b-71d68cf96fa7.png)
## การบันทึกผลการทดลอง
จากการใช้คำสั่ง pio device monitor จะเริ่มสแกนหา wifi จะขึ้นเป็นจำนวนและชื่อของwifiที่ตรวจพบ
## อภิปรายผลการทดลอง
จากการทดลองการเขียนโปรแกรมค้นหาไวไฟ จะเห็นว่าเมื่อเราอัพโหลดโปรแกรมลงในไมโครคอนโทรเลอร์ และใช้คำสั่ง pio device monitor เพื่อดูการทำงานของไมโครคอนโทรเลอร์และหน้าจอจะแสดงผลจำนวนและชื่อของwifiที่ตรวจพบ
