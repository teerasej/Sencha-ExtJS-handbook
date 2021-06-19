
# ทำความเข้าใจ View

เปิดไฟล์ **app/desktop/src/view/main/MainView.js**

```js
// function .define() กำหนดคุณสมบัติของ Class
// ส่วนแรกคือกำหนดชื่อ Class และ namespace
Ext.define('CounterApp.view.main.MainView', {

  // สืบทอดคุณสมบัติของ Container class
  extend: 'Ext.Container',

  // กำหนด xtype ชื่อ mainview ที่สามารถอ้างอิงในส่วนอื่นของแอพได้
  xtype: 'mainview',

  // กำหนดชื่อ controller ที่จะทำงานกับ View class นี้
  controller: 'mainviewcontroller',

  // กำหนด view model ที่จะทำงานกับ view class นี้
  viewModel: {
    type: 'mainviewmodel'
  },

  // Container class สามารถใส่ component ตัวอื่นลงไปได้ผ่าน item: property
  items: [
    {
      xtype: 'component',
      html: '<a style="font-size:24px" target="_blank" href="https://docs-devel.sencha.com/extjs/7.0.0-CE/guides/quick_start/What_You_Will_Be_Coding.html">Quick Start Tutorial Here</a><p>'
    },
    {
      xtype: 'displayfield',
      reference: 'df',
      bind: {
        value: '{clickTime}'
      }
    },
    {
      xtype: 'button',
      text: 'Click Me!',
      handler: 'onButtonClick'
    }
  ]
})
```

## 1. Class ในจักรวาลของ Extjs

- ExtJS มองว่าถ้า JavaScript มีการนำระบบ Class มาใช้ จะทำให้การทำงานโปรเจคขนาดใหญ่จัดการได้ง่าย 
- การสร้าง Class สามารถกำหนดโดยใช้ function `Ext.define('ชื่อ namespace ของ class', { คุณสมบัติของ class นั้นๆ })`

เช่น 

```js
          // กำหนด Namespace 
Ext.define('CounterApp.view.main.MainView', {

  // กำหนดว่ามีคุณสมบัติจาก Class ชื่อ Container ของ Extjs
  extend: 'Ext.Container',

  // กำหนด symbolic type ที่สามารถอ้างอิงได้จากส่วนอื่นของแอพพลิเคชั่น
  xtype: 'mainview',

  //...
})
```

> ดูเรื่องการกำหนด namespace [เพิ่มเติมที่นี่](../kb/namespace.md)

## 2. Container สามารถใส่ Component ตัวอื่นลงไปได้ 

- Container เป็น Component ตัวหนึ่งที่สามารถ เพิ่ม Component ตัวอื่นเข้าไปได้ 
- ในการทำเว็บเราอาจเรียก Container ว่า Parent element และ component ด้านในว่า Child element
- เราสามารถเพิ่ม Component ใน Container ได้ ผ่าน `items:[]` property

### ทดสอบเพิ่ม Component ลงไปใน MainView

```js
Ext.define('CounterApp.view.main.MainView', {
  
  //...

  items: [
    {
      xtype: 'component',
      html:'<h1>Hello World</h1>'
    },
    //...
  ]
})
```

- จะเป็นการเพิ่ม HTML ลงไปใน component แบบพื้นฐาน 
- บันทึกไฟล์ และสังเกตผลลัพธ์

## Container มี Layout 

- ไม่เหมือน div element ของ HTML ทั่วไป Container มาพร้อมกับค่า layout ที่สามารถ กำหนดได้
- ค่า `layout:` property จะมี **auto** และ **hbox**

### ทดสอบเพิ่ม layout property 

```js
Ext.define('CounterApp.view.main.MainView', {
  
    //...
    layout: 'hbox',
    //...
  ]
})
```

- บันทึกไฟล์ และสังเกตผลลัพธ์
