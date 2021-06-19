
# ทำความเข้าใจ ViewModel

เปิดไฟล์ **app/desktop/src/view/main/MainViewModel.js**

```js
Ext.define('CounterApp.view.main.MainViewModel', {

  // extend class ViewModel
  extend: 'Ext.app.ViewModel',

  // คล้ายกับ xtype แต่ชื่อนี้จะถูกนำไปใช้กับ View Class และ View Controller ได้
  alias: 'viewmodel.mainviewmodel',

  // ข้อมูลที่สามารถ binding ใน View และถูกเรียกใช้ใน ViewController ได้
  data: {
    clickTime : Date.now()
  },

  // ส่วนเชื่อม Store
  stores: {
  }
})
```

- ViewModel เป็นตัวแทนของข้อมูลที่จะถูกใช้กับ View ผ่านการ binding 
- ข้อมูลใดๆ จาก store จะใช้ใน View ต้องส่งผ่าน ViewModel
- จะมี `data:[]` property เป็นตัวส่งผ่านข้อมูลไปสู่ View 

## 1. ทดสอบสร้าง data ให้กับ View

ทดสอบเพิ่ม **name** property ให้กับ object ใน `data:` property 

```js
// app/desktop/src/view/main/MainViewModel.js
Ext.define('CounterApp.view.main.MainViewModel', {
  //...
  data: {
    //...
    name: 'Nextflow'
  },
  //...
})
```

## 2. ทำการเรียกใช้ค่าจาก ViewModel ใน View

เปิดไฟล์ MainView.js เพื่อแก้ไขให้ component Hello World ทำการ bind data ชื่อ **name** จาก ViewModel

```js
// app/desktop/src/view/main/MainView.js

Ext.define('CounterApp.view.main.MainView', {
  
  // สังเกตว่าใน View มี `viewModel` property ที่กำหนดชื่อ ชื่อไปที่ mainviewmodel อยู่ก่อนแล้ว
  viewModel: {
    type: 'mainviewmodel'
  },  

  //...

  items: [
    {
      xtype: 'component',
      // กำหนด bind property เพื่อใช้ data จาก view model ใน HTML
      bind: {
        html:'<h1>Hello {name}</h1>'
      }
    },
    //...
  ]
})
```

ทำการบันทึกไฟล์ และสังเกตผล