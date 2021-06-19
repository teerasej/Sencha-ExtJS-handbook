
# Simple Counter App 

## 1. สร้างโปรเจคใหม่ 

- [สร้างโปรเจคใหม่](1-create-project.md) และตั้งชื่อว่า simple-counter 
- รันทดสอบแอพพลิเคชั่นโดยใช้คำสั่ง `npm start`

## 2. สร้างตัวแสดง counter และปุ่มเพิ่ม

เปิดไฟล์ **app/desktop/src/view/main/MainView.js**

```js
// app/desktop/src/view/main/MainView.js

Ext.define('CounterApp.view.main.MainView', {
  extend: 'Ext.Container',
  xtype: 'mainview',
  controller: 'mainviewcontroller',
  viewModel: {
    type: 'mainviewmodel'
  },
  items: [
    // สร้างข้อความ ที่ bind ข้อมูลชื่อ count จาก viewModel
    {
        xtype: 'displayfield',
        bind: {
            value: '{count}'
        }
    },

    // แก้ไขชื่อปุ่มเป็น +1 และเรียกใช้ function onAddOne ถ้าถูกกด
    {
      xtype: 'button',
      text: '+1',
      handler: 'onAddOne'
    }
  ]
})
```

- บันทึกไฟล์ และดูผลลัพธ์ จะเห็นว่ามีปุ่ม +1 แต่ยังไม่มีตัวเลข counter แสดง

## 3. เตรียมข้อมูล counter ใน ViewModel

```js
// app/desktop/src/view/main/MainViewModel.js

Ext.define('CounterApp.view.main.MainViewModel', {
  extend: 'Ext.app.ViewModel',
  alias: 'viewmodel.mainviewmodel',
  data: {
    clickTime : Date.now(),

    // เพิ่ม count property สำหรับใช้งานใน View Model 
    count: 0
  },
  stores: {
  }
})
```

- บันทึกไฟล์ และดูผลลัพธ์ จะเห็นว่าตัวเลข counter แสดงบนหน้าเว็บในส่วนของ displayfield component แล้ว

## 4. สร้าง function เพื่อแก้ไขข้อมูลใน ViewController

เนื่องจากใน View ชื่อ **MainView.js** มีการเรียกใช้ function ชื่อ **onAddOne** 

```js
{
  xtype: 'button',
  text: '+1',
  handler: 'onAddOne'
}
```

เราจึงจะมาสร้าง function ดังกล่าวใน ViewController เพื่อให้เรียกใช้งานได้จริง

```js
// app/desktop/src/view/main/MainViewController.js

Ext.define('CounterApp.view.main.MainViewController', {
  extend: 'Ext.app.ViewController',
  alias: 'controller.mainviewcontroller',

  onButtonClick: function (button) {
    this.lookupReference('df').setValue(Date.now())
  }

  // สร้าง function onAddOne
  onAddOne: function (button) {

    // ใช้ function getViewModel() หากไม่ระบุชื่อ จะใช้ viewmodel ตัวที่กำหนดไว้ใน View
    // และเข้าถึงส่วน data ชื่อ count
    let a = this.getViewModel().data.count
    console.log(a)

    // กำหนดค่าใหม่ให้ data ชื่อ count ใน ViewModel
    this.getViewModel().set('count', a + 1)
  }

})

```

- บันทึกไฟล์ และดูผลลัพธ์ จะเห็นว่ากดปุ่มแล้วตัวเลข counter จะเพิ่มจำนวนเองแล้ว