
# ทำความเข้าใจ ViewController

เปิดไฟล์ **app/desktop/src/view/main/MainViewController.js**

```js
Ext.define('CounterApp.view.main.MainViewController', {

  // สืบทอดคุณสมบัติของ ViewController class
  extend: 'Ext.app.ViewController',

  // คล้ายกับ xtype แต่ชื่อนี้จะถูกนำไปใช้กับ View Class และ View Controller ได้
  alias: 'controller.mainviewcontroller',

  // กำหนด function ที่สามารถเรียกใช้จาก View ได้
  onButtonClick: function (button) {

    // function .lookupReference() ใช้ในการมองหา child component ใน View นั้นๆ 
    this.lookupReference('df').setValue(Date.now())
  }

})
```

- ในที่นี้ ViewController มักเป็นที่ที่เราจะเตรียม function ที่จะทำงานจาก action ใน View 
- เราสามารถเข้าถึง/อัพเดตข้อมูลใน View หรือ ViewModel ก็ได้

จะเห็นว่ามีการประกาศ function ชื่อ `onButtonClick` ในไฟล์  **MainViewController.js** ซึ่งมีการอ้างอิงและเรียกใช้ในไฟล์ **MainView.js** ดังด้านล่าง

```js
Ext.define('CounterApp.view.main.MainView', {
  
  //...
  
  // กำหนดเรียกใช้ Controller ชื่อ mainviewcontroller ตามที่ถูกตั้งเป็น alias ไว้ในไฟล์ MainViewController.js
  controller: 'mainviewcontroller',
  
  //...

  items: [
    //...
    // กำหนดสร้างปุ่ม 
    {
      xtype: 'button',
      text: 'Click Me!',

      // กำหนด handler property เป็นชื่อของ function ที่อยู่ใน mainviewcontroller เพื่อเรียกใช้
      handler: 'onButtonClick'
    }
  ]
})

```


## 1. ทดสอบอัพเดตข้อมูลใน ViewModel

ให้เพิ่มคำสั่งลงไปใน function `onButtonClick` ของ **MainViewController**

```js
// app/desktop/src/view/main/MainViewController.js
Ext.define('CounterApp.view.main.MainViewController', {
  extend: 'Ext.app.ViewController',
  alias: 'controller.mainviewcontroller',

  onButtonClick: function (button) {
    this.lookupReference('df').setValue(Date.now())
    
    // เรียกใช้ ViewModel ชื่อ mainviewmodel และกำหนดชื่อ data 'name' ด้วยข้อความใหม่
    this.getViewModel('mainviewmodel').set('name','ExtJS')
  }

})

```

ทำการบันทึกไฟล์ กดปุ่ม click me และสังเกตผล