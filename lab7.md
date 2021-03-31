# การทดลองที่ 7 การควบคุมการ เปิด-ปิด ผ่าน wifi
## วัตถุประสงค์
1. เพื่อสร้างและพัฒนาเครื่องควบคุมเปิด-ปิดปลั๊กไฟผ่าน WiFi
2. เพื่อศึกษาการทำงานชุดควบคุมการเปิด-ปิด
## อุปกร์ที่ใช้ทดลอง
1. บอร์ด NodeMCU V2
2. Solid State Relay SSR Module
3. สายไฟจัมเปอร์
4. ปลั๊กไฟ
5. แผ่นอะคริลิค
## ศึกษาข้อมูลเพิ่มเติมจาก
1. http://sv.mtc.ac.th/inno/files/YYYYYYYYYYYYYYYYYYYY.pdf
2. https://github.com/choompol-boonmee/lab63b/tree/master/examples
## วิธีการทำการทดลอง
1. นำบอร์ดมาต่อเข้ากับรีเลย
2. นำทั้งสองมาต่อเข้ากับปลั๊กไฟดังรูป
![alt text](https://cdn.discordapp.com/attachments/823124660014940180/826833709981237278/1.jpg)
3. ประกอบบอร์ดใส่กล่องและอัพโหลดโค้ดลงในบอร์ด
โดยภาษาที่เขียนโค้ดคือ ภาษา C ชุดคำสั่งมีดังนี้
```
# include <ESP8266WiFi.h>
const char* ssid = "AndroidAP";
const char* password = "12345678";
int ledPin = 13; // GPIO13 Arduino = D7 NodeMCU
WiFiServer server(80);
void setup() {
Serial.begin(115200);
delay(10);
pinMode(ledPin, OUTPUT);
digitalWrite(ledPin, LOW);
// Connect to WiFi network
Serial.println();
Serial.println();
Serial.print("Connecting to ");
Serial.println(ssid);
WiFi.begin(ssid, password);
while (WiFi.status() != WL_CONNECTED) {
delay(500);
Serial.print(".");
} 
Serial.println("");
Serial.println("WiFi connected")
// Start the server
server.begin();
Serial.println("Server started");
// Print the IP address
Serial.print("Use this URL to connect: ");
Serial.print("http://");
Serial.print(WiFi.localIP());
Serial.println("/");
}
void loop() {
// Check if a client has connected
WiFiClient client = server.available();
if (!client) {
return;
}
// Wait until the client sends some data
Serial.println("new client");
while(!client.available()){
delay(1);
}
// Read the first line of the request
String request = client.readStringUntil('\r'); 
Serial.println(request);
client.flush();
// Match the request
int value = LOW;
if (request.indexOf("/LED=ON") != -1) {
digitalWrite(ledPin, HIGH);
value = HIGH;
}
if (request.indexOf("/LED=OFF") != -1) {
digitalWrite(ledPin, LOW);
value = LOW;
}
// Set ledPin according to the request
//digitalWrite(ledPin, value);
// Return the response
client.println("HTTP/1.1 200 OK");
client.println("Content-Type: text/html");
client.println(""); // do not forget this one
client.println("<!DOCTYPE HTML>");
client.println("<html>");
client.print("Led pin is now: ");
if(value == HIGH) { 
client.print("On");
}else { client.print("Off");
}
client.println("<br><br>");
client.println("<a href=\"/LED=ON\"\"><button>Turn Off </button></a>");
client.println("<a href=\"/LED=OFF\"\"><button>Turn On </button></a><br />");
client.println("</html>");
delay(1);
Serial.println("Client disonnected");
Serial.println("");
}
```
4. จากนั้นเปิด Serial Monitor(รูปแว่นขยาย)ที่มุมขวาบน จากนั้นตั้งค่า Monitor รอสักครู่จะได้ URL
5. นำ URL ที่ได้ไปใส่ที่ Web Browser จากการทดลองนี้จะได้ http://192.168.43.10/ ซึ่งจะได้ผลลัพธ์ดังนี้
![alt text](https://cdn.discordapp.com/attachments/823124660014940180/826835486604656640/2.jpg)
## บันทึกผลการทดลอง
จากผลการทดลอง ชุดทดลองทำงานไปตามปกติ สามารถนำใช้งานได้กับ พัดลม,กระทะไฟฟ้า,กาต้มน้ำ,เตารีด,ทีวี,หม้อหุงข้าว ได้
## อภิปรายผลการทดลอง
เนื่องจากปัญหาโรคระบาด Covid-19 ทำให้การทดลองเป็นไปได้ยากเนื่องจากไม่มีอุปกรณ์ที่จะทำการทดลอง ความรู้ที่นำมาประยุกต์ใช้ในการทดลองที่7 อาจมีข้อผิดพลาดได้หลายๆจุด ดังนั้นการทดลองที่7จึงเป็นการประยุกต์มาจากการทดลองที่1-6แล้วการหาความรู้เพิ่มจากอินเตอร์เน็ต
## คำถามหลังการทดลอง
ลิงค์ URL ที่ได้มา มีไว้ทำอะไร
1. Ans : มีไว้ใส่ในweb browser เพื่อควบคุมการเปิด-ปิดปลั๊กไฟ

