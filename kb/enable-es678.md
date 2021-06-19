
# การเปิดใช้งาน ES6/7/8 ใน Sencha CMD

**Sencha CMD และ ExtJS ตั้งแต่เวอร์ชั่น 6.5.2 ขึ้นไป**จะรองรับ รองรับการแปลงโค้ด JavaScript เวอร์ชั่น ES6/7/8 ใช้งาน

สามารถทำได้โดยการเพิ่มค่า setting เข้าไปใน `app.json` 

```json
{
    ...

    "language": {
        "js": {
            "input": "ES8",
            "output": "ES5"
        }
    },
}
```

อ้างอิง

- https://www.sencha.com/blog/announcing-ext-js-6-5-2-sencha-cmd-6-5-2-ga/ 