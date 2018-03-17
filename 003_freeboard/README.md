Installation
-----

วิธีแรก  
Nodered > Manage Pallette > 'node-red-contrib-freeboard'
  
[วิธีที่สอง](https://flows.nodered.org/node/node-red-contrib-freeboard)  

เข้าไปที่ folder home ของ nodered แล้วตดตั้งผ่าน npm
```
cd C:\Users\Napat\.node-red
npm install node-red-contrib-freeboard
```

แต่ในบางเวอร์ชั่น (0.0.7) [พบปัญหาในการติดตั้ง](https://github.com/urbiworx/node-red-contrib-freeboard/issues/22) ให้ติดตั้งด้วยวิธีที่สามดังนี้
```
cd C:\Users\Napat\.node-red
npm install -g node-red-contrib-freeboard
```

สั่งรัน nodered โดยใช้ชื่อ project เป็น hellofreeboard
```
node-red hellofreeboard
``` 

เปิด freeboard ขึ้นมาได้จาก url `http://127.0.0.1:1880/freeboard/`

สรุปแบบสั้นๆ
-----
1. `hellofreeboard.json` คือไฟล์ของ nodered ที่ใช้ในโปรเจคนี้สามารถ import หรือ copy ข้อมูลภายในไปเปิดด้วย nodered ได้เลย
2. `freeboard_start-79981.json` คือไฟล์สำหรับ nodred-freeboard ให้นำไปวางไว้ที่ home dir ของ nodered เช่น `C:\Users\Napat\.node-red\freeboard_start-79981.json` 
3. เข้าสู่หน้า freeboard ได้ที่ url `http://127.0.0.1:1880/freeboard/#start-79981` 

Tutorial
-----
ในหน้าออกแบบ flow จะมี node ชื่อ freeboard อยู่ใน advanced สามารถส่งค่าเข้า freeboard ผ่านทาง node ดังกล่าวได้เลย  
ข้อมูลจะไปปรากฏอยู่ที่ datasources ของ freeboard ตามชื่อ node ที่ตั้งเอาไว้  

ในหน้า freeboard ให้ทำการเพิ่ม datasouces และตั้ง `Name` ที่จะใช้ใน freeboard ui  จากนั้นให้ทำการ `ADD PANE` ขึ้นมาและสั่งเพิ่ม `WIDGET` โดยการกดเครื่องหมาย `+` ของ pane เลือกชนิดของ widget และกำหนด datasources จากชื่อที่ได้ตั้งเอาไว้ให้เรียบร้อยก็จะสามารถแสดงผลได้เรียบร้อย

*ระวัง* freeboard จะไม่ save อัตโนมัติ หากสั่ง refresh ไปหน้า ui ที่ออกแบบไว้ก็จะหายไปหมดเลย  

การ save freeboard
-----
ทำได้โดยการกดป่ม SAVE FREEBOARD แล้วจะมีตัวเลือกขึ้นมาสองแบบคือ PRETTY และ MINIFIED ทั้งสองตัวเลือกจะถูก save เป็นไฟล์แบบ json ทั้งคู่ ความแตกต่างของทั้งสองแบบก็คือ  
1. แบบ PRETTY เมื่อเปิดไฟล์ด้วย editor แล้วจะอ่านข้อมูลภายใน json ได้ง่าย มีการเว้นวรรคหรือแท็บให้อย่างสวยงาม  
2. แบบ MINIFIED เป็นการ save โดยต้องการลดขนาดของไฟล์ json ให้เล็กที่สุดทำให้เมื่อเปิดอ่านจะอ่านยากมาก  

ในที่นี้แนะนำให้เลือกเป็นแบบ MINIFIED เพราะเราไม่ได้จะเข้าไปอ่าน/เขียนไฟล์ดังกล่าวอยู่แล้ว

หลังจากกดปุ่ม PRETTY หรือ MINIFIED เราจะได้ url ขึ้นมาใหม่เช่น http://127.0.0.1:1880/freeboard/#start-79981 ซึ่งสามารถกลับมาเปิดได้ในภายหลัง  
ในตัวอย่างนี้ข้อมูล freeboard จะถูกเก็บอยู่ที่ `C:\Users\Napat\.node-red\freeboard_start-79981.json` หากจำ url ไม่ได้ก็สามารถเข้าไปดูจากชื่อได้ที่ path ดังกล่าว

การเพิ่ม widget ให้ freeboard
-----

Freeboard ของ nodered นั้นสามารถเพิ่ม widget เข้าไปเพิ่มเติมได้  
โดยเราสามารถสร้าง widget ขึ้นมาเองหรืออาจจะไปดาว์โหลดจากในอินเตอร์เน็ทมาใช้งานก็ได้ (ดูหัวข้อ Widget Reference เพิ่มเติม)  
ซึ่งไฟล์ widget จะมีนามสกุลเป็น .js เช่น actuator.js / switch.js เป็นต้น  

ขั้นตอนการติดตั้ง widget เราจะต้องไปใส่ไว้ใน `freeboard\plugins`  
ซึ่งจะต้องหา path ของ `node-red-contrib-freeboard` ให้เจอซะก่อน โดยจะแตกต่างกันไปในแต่ละเครื่อง เช่น    
หากติดตั้ง node-red-contrib-freeboard ด้วย npm -g (global) บน Windows10 จะอยู่ที่  
`C:\Users\Napat\AppData\Roaming\npm\node_modules\node-red-contrib-freeboard` 
ภายในจะมี subdirectory `node_modules\freeboard\plugins` อยู่ให้เราทำการวางไฟล์ widget .js ไปไว้ใน path ดังกล่าว ตัวอย่างเช่น  

```
C:\Users\Napat\AppData\Roaming\npm\node_modules\node-red-contrib-freeboard\node_modules\freeboard\plugins\actuator.js

C:\Users\Napat\AppData\Roaming\npm\node_modules\node-red-contrib-freeboard\node_modules\freeboard\plugins\switch.js
```

จากนั้นให้ทำการแก้ไขไฟล์ `C:\Users\Napat\AppData\Roaming\npm\node_modules\node-red-contrib-freeboard\node_modules\freeboard\index.html` 
เพื่อให้รู้จัก plugin ที่ติดตั้งเพิ่มเข้าไป โดยให้เพิ่มเข้าไปในส่วนของ `head.js` ตัวอย่างเช่น

จากเดิม
```
    <script type="text/javascript">
        head.js("js/freeboard.js","js/freeboard.plugins.min.js", "../freeboard_api/datasources"
                , "plugins/thirdparty/jquery.keyframes.min.js", "plugins/thirdparty/widget.ragIndicator.js",
            function () {
                $(function ()            
```  

หลังจากแก้ไขจะกลายเป็น
```
    <script type="text/javascript">
        head.js("js/freeboard.js","js/freeboard.plugins.min.js", "../freeboard_api/datasources", 
                "plugins/thirdparty/jquery.keyframes.min.js", "plugins/thirdparty/widget.ragIndicator.js", 
                "plugins/actuator.js", 
                "plugins/plugin_highcharts.js", 
                "plugins/slider_plugin.js",
                "plugins/switch.js", 
                "plugins/widget_tables.js", 
            function () {
                $(function ()
```
์Note: ต้องมี `,` ปิดท้ายด้วย

ภายใน `/freeboard` > ADD PANE > WIDGET ก็จะมีลิสของ widget ที่เพิ่มเข้ามาให้ใช้งาน  

#### Widget: Slider [in/out]
สามารถเป็นได้ทั้ง input และ output การใช้งาน slider รับค่าจาก datasourse แบบง่ายๆก็ใช้งานได้แบบ widget อื่นๆทั่วไป  
การใช้งานเป็น output เพื่อส่งค่าจาก slider ออกไปยัง http in ของ nodered มีรายละเอียดการใช้งานที่ต้องทราบอยู่บ้างดังนี้
ภายใน widget setting ของ slider จะมีช่อง `URL ON CHANGED` อยู่ซึ่งจะใช้ส่งค่าไยัง http หรือ webhook ทั่วไปได้ ตัวอย่างการป้อนค่าจะเป็นประมาณนี้
`http://127.0.0.1:1880/sliderval?dat=%VALUE%`  
จากนั้นในหน้า node-red ให้ไปเพิ่ม `1.http in <--> 2.http response & 3.debug` สามโหนดให้เรียบร้อย  
Note: หากไม่ได้ต่อโหนด http response เมื่อ slider เรียก web hook แล้วจะไม่มี response กลับมาทำให้เกิดปัญหาการรอ response ในหน้า freeboard ไปเรื่อยๆขึ้น  

#### Widget: Switch [out]
ใน Setting จะมีช่อง `URL ON` และ `URL OFF` เพื่อส่งค่าออกไปเมื่อ switch ถูก on/off  
แสดงตัวอย่างการตั้งค่าเพื่อเรียก webhook ได้ดังนี้  
```
URL ON:     http://127.0.0.1:1880/switch01?enable=on
URL OFF:    http://127.0.0.1:1880/switch01?enable=off
```


#### Widget: Actuator [in/out]
จะคล้ายๆกับ `Indicator Light` ซึ่งเป็น Default Widget ที่มากับ freeboard อยู่แล้ว 
ข้อแตกต่างคือ `Actuator` มีการเพิ่ม setting หัวข้อ `URL ON` และ `URL OFF` เข้าไปเพื่อใช้ส่งค่าออกไปยัง url ของ webhook เมื่อเกิด event on/off ได้
การใช้งานก็เหมือนทั่วไปคือ
```
# datasource input เพื่อรับค่าเข้ามาควบคุม on/off
VALUE:      datasources["lightstatus"] 
# webhook output สามารถปล่อยว่างไว้ได้ หรือจะใส่ค่าก็ได้แต่ต้องมีตัว http webhook คอย response
URL ON:     http://127.0.0.1:1880/lightfeedback01?isenable=1
URL OFF:    http://127.0.0.1:1880/lightfeedback01?isenable=0
```

Reference
-----
- http://noderedguide.com/tag/freeboard/
- [freeboard widget example](https://github.com/Freeboard/plugins/tree/master/widgets)  
- [Additional widgets](https://github.com/Freeboard/freeboard/wiki)   
- [actuator.js / plugin_highcharts.js / slider-plugin.js / switch.js ](https://github.com/onlinux/freeboard-plugins)
- [widget.tables.js](https://github.com/daleroy1/freeboard-table)

