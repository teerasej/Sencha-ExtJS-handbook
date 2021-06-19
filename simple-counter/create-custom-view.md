
## การประกาศ Class และ Namespace

นี่คือรูปแบบของ การประกาศ Class ชื่อ `MainView` โดยใช้ function ที่ชื่อ `Ext.define()`

```js
// ที่อยู่ของ
Ext.define('CounterApp.view.main.MainView', {})
```

- หลักการตั้งชื่อ Namespace คือ **<ชื่อ Application>.<ชื่อโฟลเดอร์>.<ชื่อ Class>**
- ที่อยู่ของไฟล์ในโปรเจคคือ **app/desktop/src/view/main/MainView.js** 
- แต่เวลาอ้างอิง เราจะอ้างกับที่อยู่ของ ไฟล์ **Application.js** ทำให้ได้เป็น **view/main/MainView.js** 


## การสร้าง Class ที่เป็น View หรือ UI

ExtJS มี Class ที่เป็น UI พร้อมอยู่แล้ว ขึ้นอยู่กับว่าเราต้องการกำหนดใช้ Class ของเราเป็น UI ตัวไหน 

สามารถกำหนดได้ โดยใส่เป็นชื่อ ใน property ชื่อ `extend:` เช่น ด้านล่างกำหนดเป็น `Ext.Container` ([Container](https://docs.sencha.com/extjs/7.0.0/modern/Ext.Container.html)) 

```js
Ext.define('CounterApp.view.main.MainView', {
    extend: 'Ext.Container'
})
```