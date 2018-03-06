การ Import and Export flow 
------
Flow จะถูก save อยู่ในรูปของไฟล์ json ในเวอร์ชันปัจจุบันสามารถ import/export ได้สองวิธีคือ 
1. ผ่าน clipboard  
เป็นการ copy & paste json text file ของ flow ทั้งอันเพื่อ import/export flow เข้ามายังโปรเจค  
2. ผ่าน Library  
เป็นการ save ลงใน home folder ของ nodered (nodered home ปกติจะอยู่ที่ ~/.node-red/) 
path ที่อยู่จะประมาณนี้ `~/.node-red/lib/flows/` 
ขั้นตอนในการ save flow ให้ select node elements ที่ต้องการ save(ใช้ ctrl+a เพื่อ select all ได้) 
จากนั้นเลือก Export > Library และกรอกชื่อ foldername/flowname ที่ต้องการลงไป  
ขั้นตอนการ load ให้เข้าไปที่ Import > Library > floder/flow ที่ต้องการใช้งาน  


Subflow
-----
เป็นการสร้าง custom node ใช้งาน เพื่อความง่ายอาจจะมองว่าเป็นการยุบรวมเอา nodes หลายๆโหนดเข้าด้วยกันให้เหลือเพียงโหนดเดียว
เพื่อลดความซับซ้อน สามารถนำไปใช้ซ้ำได้ง่่ายและทำให้มองเห็นภาพรวมของโปรเจคได้ดียิ่งขึ้น 
ตัวอย่างการใช้ subflow เช่น การสร้าง node ที่รับค่าอุณหภูมิจากองศาเซลเซียสจากโปรโตคอล mqtt(sub) ตรวจสอบข้อมูล และคืนค่าเป็นองศาฟาเรนไฮต์ เป็นต้น


Dashboard UI
-----
หลังจากลง `node-red-dashboard` เพิ่มแล้วจะสามารถเข้าไปดู ui ได้ที่ `http://127.0.0.1:1880/ui/`  
ค่าที่ต้องทำความเข้าใจหลักๆคือ 
1. Tab ภายในจะสามารถมี Group อยู่ภายในได้หลายๆ Groups
2. Group ภายในจะประกอบไปด้วย ui node หลายๆอันอยู่
3. Order ของ node เป็นตัวกำหนดว่า node จะได้อยู่ส่วนใดของ UI Group นั้นๆ เวลาแสดงผลจะเรียงตามหมายเลขจากซ้ายไปขวา/บนลงล่าง  


RPI: Rasbian
-----
Rasbian OS จะติดตั้ง nodered และ lib สำหรับควบคุมฟังก์ชันพื้นฐานของ rPi เช่น gpio มาให้อยู่แล้ว 
  
  
Ref
-----
- https://flows.nodered.org/

