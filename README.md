
การรัน nodered
------
หลังจากติดตั้ง nodered เสร็จเรียบร้อย เราสามารถสั่งรันได้ด้วยคำสั่ง 
`node-red` และเปิดเข้าไปใช้งานที่ `http://127.0.0.1:1880` ได้เลยทันที   

แต่มีทริกนิดนึงคือ ในตอนที่ใช้งานจริงเราจะได้ต้องออกแบบ flow แยกสำหรับ project ต่างๆกันอยู่แล้ว เช่น
project01, project02, project03 
หากเรารันด้วย `node-red` ปกติจะทำให้หน้าจอการออกแบบปนกันไปหมด  
เราสามารถแก้ปัญหาได้ด้วยการเพิ่ม argument ตามหลังเข้าไปตอนสั่ง nodered ทำงานเช่น  
`node-red project01`, `node-red project02`, `node-red project03`   ก็จะสามารถแยกหน้าสำหรับออกแบบออกจากกันได้เรียบร้อย  
จากตัวอย่างจะเกิดไฟล์ขึ้นมาใหม่ 3 ไฟล์ที่ home directory ของ nodered ดังนี้
```
C:\Users\Napat\.node-red\project01
C:\Users\Napat\.node-red\project02
C:\Users\Napat\.node-red\project03
```

nodered with docker
-----
มี doc เขียนไว้ดีมากอยู่แล้วสามามารถไปอ่านได้ที่ [link](https://hub.docker.com/r/nodered/node-red-docker/)
สรุปเป็นคำสั่งสั้นๆสำหรับการทำโปรเจคในโปรเจคใดๆได้ง่ายๆดังนี้
```
cd <your project>
mkdir -p node_red_user_data
docker run --rm -it -p 1880:1880 -v node_red_user_data:/data --name mynodered nodered/node-red-docker
```
Note: ไม่แนะนำให้ใช้ nodered+docker สำหรับมือใหม่หัดใช้เนื่องจากอาจจะต้อง customize env เช่น port ต่างๆเพิ่มเติมตามความต้องการของแต่ละโปรเจค และอาจจะงงเรื่อง path หรือตำแหน่งไฟล์ต่างๆ
 

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
  
Nodered node pkg
-----
- Dashboard https://flows.nodered.org/node/node-red-dashboard
- MQTT broker https://flows.nodered.org/node/node-red-contrib-mqtt-broker

Ref
-----
- https://flows.nodered.org/

