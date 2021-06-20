
# สร้าง model และ store

## 1.  สร้าง model เป็นตัวแทนของข้อมูล note

สร้างไฟล์ **app/desktop/src/model/Note.js**

```js
// ตั้งชื่อตามหลักการกำหนด namespace
Ext.define('CounterApp.model.Note',{

    // extend model class
    extend: 'Ext.data.Model',

    // กำหนด field ของ model
    fields: [
        {name: 'message',  type: 'string'}
    ]
})
```

## 2. สร้าง store เพื่อ feed ข้อมูล 


สร้างไฟล์ **app/desktop/src/store/Notes.js**

```js
Ext.define('CounterApp.store.Notes',{
    extend: 'Ext.data.Store',
    alias: 'store.notes',

    // เรียกใช้ model Note ที่สร้างไว้ 
    model: 'CounterApp.model.Note',

    // กำหนด storeId เพื่อให้สามารถเรียกใช้ได้จากภายใน Application 
    storeId: 'notes',

    // กำหนดข้อมูลเริ่มต้น ผ่าน property data
    data: [
        { message: '1' },
        { message: '2' },
        { message: '3' },
        { message: '4' },
        { message: '5' },
        { message: '6' },
        { message: '7' },
        { message: '8' },
        { message: '9' },
        { message: '10' }
    ]
})
```