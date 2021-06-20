

# สร้าง User Interface 

## 1. กำหนด layout center ให้ container


```js
// app/desktop/src/view/main/MainView.js

Ext.define('CounterApp.view.main.MainView', {
  extend: 'Ext.Container',
  xtype: 'mainview',

  controller: 'mainviewcontroller',
  viewModel: {
    type: 'mainviewmodel'
  },

  // กำหนด Layout ของ container เป็น center
  layout: 'center',

  items: [
    //...
  ]
})


```

## 2. สร้าง panel ไว้ใน container

```js
// app/desktop/src/view/main/MainView.js

Ext.define('CounterApp.view.main.MainView', {
  extend: 'Ext.Container',
  xtype: 'mainview',

  requires: [
    'Ext.layout.Center'
  ],

  controller: 'mainviewcontroller',
  viewModel: {
    type: 'mainviewmodel'
  },

  layout: 'center',

  items: [

    // เรียกใช้ panel component และกำหนดคุณสมบัติต่างๆ 
    {
      xtype: 'panel',
      width: 600,
      height: 450,
      title: 'Note List',
      shadow: 'true'
    }
  ]
})

```