## การทดลองที่ 1 เรื่อง การเขียนโปรแกรมเพื่อรันบนไมโครคอนโทรเลอร์
# วัตถุประสงค์
1) เพื่อศึกษาเกี่ยวกับการทำงานและการเชื่อมต่อเบื้องต้นของไมโครคอนโทรเลอร์
2) เพื่อศึกษาเกี่ยวกับการ run ไมโครคอนโทรเลอร์
# อุปกรณ์ที่ใช้
1) คอมพิวเตอร์
2) ไมโครคอนโทรเลอร์ ESP01
3) อุปกรณ์ต่อ USB-Serial
# ศึกษาข้อมูลเบื้องต้น
1) run example 1 https://youtu.be/NLIUsWLEpmg
2) code 01_Serial-Monitor https://github.com/choompol-boonmee/lab63b/blob/master/examples/01_Serial-Monitor/src/main.cpp
# วิธีทำการทดลอง
1) เชื่อมต่อไมโครคอนโทรเลอร์เข้ากับคอมพิวเตอร์ด้วยการต่อ USBไปยังSerial
![alt text](https://cdn.discordapp.com/attachments/663373978848591875/824214658948530176/112262904-f9e32100-8ca0-11eb-9f47-268601cf5927.png)
2) เปิด cmd ซึ่งจากตัวอย่างอยู้ในโฟล์เดอร์ ใช้คำสั่ง cd pattani
![alt text](https://cdn.discordapp.com/attachments/663373978848591875/824215655830126602/112263053-3b73cc00-8ca1-11eb-9208-d6c6f034ab40.png)
3) ใช้คำสั่ง cd_Serial-Monitor ตามด้วย vi srv/main.cpp เพื่อการดูและศึกษาโค้ดตัวอย่างโปรแกรมที่ใช้ในการทดสอบ microcontroller
![alt text](https://cdn.discordapp.com/attachments/663373978848591875/824218014760173578/unknown.png)
4) ใช้คำสั่ง vi platformio.ini เพื่อให้ทราบข้อมูลเกี่ยวกับไมโครคอนโทรเลอร์
5) ใช้คำสั่ง pio run -t upload เพื่อทำการรันไมโครคอนโทรเลอร์
6) กดที่ปุ่มของไมโครคอนโทรเลอร์ เพื่อให้โปรแกรมรับคำสั่งใหม่เข้าไป
![alt text](https://cdn.discordapp.com/attachments/663373978848591875/824218369196032010/112263157-6a8a3d80-8ca1-11eb-95f8-a52ef839065b.png)
7) หากขึ้น success ให้ใช้คำสั่ง pio device monitor
8) รอดูผลการทดลอง
![alt text](https://cdn.discordapp.com/attachments/663373978848591875/824218710511321109/112263245-9279a100-8ca1-11eb-88c0-53347d55686d.png)
