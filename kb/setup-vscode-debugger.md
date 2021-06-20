
# การตั้งค่า Debugger ใน Visual Studio Code 

## ติดตั้ง VScode Extension 

1. ติดตั้ง Extension ชื่อ [Debugger for Chrome](https://marketplace.visualstudio.com/items?itemName=msjsdiag.debugger-for-chrome) 
2. การรัน debug mode บน chrome dev tools จะเป็นการเปิด Google Chrome เป็น Web Browser หลัก

## การสร้าง Debug Configuration

เราสามารถสร้าง Debug Configuration ได้ 2 แบบ

1. แบบที่ต้องรัน server ขึ้นมาก่อน และค่อยรัน debug session เชื่อมกัน server (attach process)
2. แบบที่สามารถสั่งรัน server ขึ้นมา จากการเริ่ม debug session เลย

### 1. แบบที่ต้องรัน server ขึ้นมาก่อน และค่อยรัน debug session เชื่อมกัน server (attach process) 

เปิดไปที่ Run and Debug ของโปรแกรม Visual Studio Code ปกติจะไม่มี Configuration อยู่ ให้กดปุ่ม **Run & Debug** เพื่อสร้าง Configuration Profile 

เราจะได้ไฟล์ **launch.json** มาแบบด้านล่าง ในที่นี้เราต้องกำหนด port ของ server ที่รันโปรเจคเราให้ถูกต้อง

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "pwa-chrome",
            "request": "launch",
            "name": "Launch Chrome against localhost",

            // ต้องแก้ port ตรงนี้ให้ตรงกับของโปรเจคเราจริงๆ ตอนที่รันคำสั่ง npm start
            "url": "http://localhost:8080",
            "webRoot": "${workspaceFolder}"
        }
    ]
}
```

ดังนั้นให้รันโปรเจคจาก Terminal ด้วยคำสั่ง `npm start` 
จะมีบรรทัดหนึ่งที่ แสดง port ของ server ที่รันโปรเจคเราอยู่ 

```bash
｢wds｣: Project is running at http://0.0.0.0:1962/
```

เช่นในที่นี่ port คือ 1962 ให้เอามาใส่แทนที่ port ของ **url** property เดิมในไฟล์ **launch.json** 

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "pwa-chrome",
            "request": "launch",
            "name": "Launch Chrome against localhost",

            // ต้องแก้ port ให้ตรงกับที่รันโปรเจคเราจริงๆ 
            "url": "http://localhost:1962",
            "webRoot": "${workspaceFolder}"
        }
    ]
}
```

ด้วยวิธีการนี้ **เราสามารถรันโปรเจคขึ้นมาด้วยการรันคำสั่ง npm start จาก Terminal ก่อน** แล้วค่อยกด Start Debug Session จากใน Visual Studio Code

จากนั้นก็สามารถวาง breakpoint และใช้งาน Debug session ได้

### 2. แบบที่สามารถสั่งรัน server ขึ้นมา จากการเริ่ม debug session

หากต้องการรัน Debug session ขึ้นมาพร้อมๆ กับการรัน server ให้แน่ใจว่าเราได้สร้างไฟล์ **launch.json** ตามขั้นตอนที่ 1 แล้ว

ให้เพิ่มเติมค่าลงไปในไฟล์ launch.json ว่า 

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "pwa-chrome",
            "request": "launch",
            "name": "Launch Chrome against localhost",

            // อย่าลืมว่า port ต้องตรงกับเวลาที่เรารันโปรเจคปกติ
            "url": "http://localhost:1962",
            "webRoot": "${workspaceFolder}",

            // เพิ่มค่านี้
            "preLaunchTask": "npm start"
        }
    ]
}
```

หลังจากนั้น ถ้ากดรัน Debug VSCode จะฟ้องว่าไม่มีส่วน tasks (คล้ายๆ เกิด error ไม่ต้องตกใจ คาดการณ์ไว้แล้ว) 

ตรงนี้จะมีการสร้างไฟล์ชื่อ **tasks.json** ขึ้นมา

ในไฟล์ **tasks.json** ที่ถูกสร้างขึ้นมา ให้แทนที่ด้วยโค้ดด้านล่าง และบันทึกไฟล์

```json
{
	"version": "2.0.0",
	"tasks": [
		{
			"type": "npm",
			"script": "start",
			"group": {
				"kind": "test",
				"isDefault": true
			},
			"isBackground": true,                      
			"problemMatcher": {
				"owner": "custom",                     
				"pattern": {
					"regexp": "^$"                     
				},
				"background": {
					"activeOnStart": true,
					"beginsPattern": "Compiling...",   
					"endsPattern": "Compiled .*"       
				}
			}
		}
	]
}
```

กลับมาที่ไฟล์ **launch.json** ให้ทำการปรับแต่งในส่วนของ **preLaunchTask** property

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "pwa-chrome",
            "request": "launch",
            "name": "Launch Chrome against localhost",

            // อย่าลืมว่า port ต้องตรงกับเวลาที่เรารันโปรเจคปกติ
            "url": "http://localhost:1962",
            "webRoot": "${workspaceFolder}",

            // แก้ไขให้มีเครื่องหมาย `:` อยู่ต่อท้ายคำสั่ง npm
            "preLaunchTask": "npm: start"
        }
    ]
}
```

บันทึกไฟล์ จากนี้การรัน debug session จะทำให้มีการรันคำสั่ง npm start ด้วย เมื่อ server รันขึ้นมาสมบูรณ์แล้ว debug session ก็จะต่อเข้ากับ server เอง

อ้างอิง - [Sencha Blog](https://www.sencha.com/blog/debugging-ext-js-applications-using-visual-studio-code-and-google-chrome/)