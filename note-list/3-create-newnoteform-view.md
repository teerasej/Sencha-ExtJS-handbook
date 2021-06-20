
# สร้าง New Note Form View และเอามาใช้ใน Main View

## 1. คำสั่งสร้าง View Package

เปิด Terminal ขึ้นมาภายในโฟลเดอร์ของโปรเจค และรันคำสั่ง

```
ext-build generate viewpackage desktop newnoteform
```

เป็นการสร้าง package ของ View 1 ชุด ซึ่งสามารถกำหนดชื่อได้ ในที่นี้กำหนดเป็น **newnoteform**

ซึ่งเราจะได้ไฟล์ขึ้นมาดังนี้ 

1. NewnoteformView.js
2. NewnoteformView.css
3. NewnoteformViewController.js
4. NewnoteformViewModel.js

## 2. นำ newnoteform มาใช้ใน MainView.js


```js
// app/desktop/src/view/main/MainView.js

Ext.define('CounterApp.view.main.MainView', {
  extend: 'Ext.Container',
  xtype: 'mainview',

  controller: 'mainviewcontroller',
  viewModel: {
    type: 'mainviewmodel'
  },

  layout: 'center',

  items: [
    {
      xtype: 'panel',
      width: 600,
      height: 450,
      title: 'Note List',
      shadow: 'true',

      // เพิ่ม padding 
      padding: 10,
      // เรียกใช้ newnoteformview (ชื่อ xtype) เพิ่มเข้ามาใน container 
      items: [
        {
          xtype: 'newnoteformview'
        }
      ]
    }
  ]
})

```

## 3.ปรับหน้าตาของ Newnoteformview 

- แปลง component จาก panel เป็น container 

```js
// app/desktop/src/view/newnoteform/NewnoteformView.js

Ext.define('CounterApp.view.newnoteform.NewnoteformView',{
	xtype: 'newnoteformview',
	cls: 'newnoteformview',
	controller: {type: 'newnoteformviewcontroller'},
	viewModel: {type: 'newnoteformviewmodel'},
	requires: [],

    // เปลี่ยนจาก Panel เป็น Ext.Container
	extend: 'Ext.Container',

	html: '<div style="font-size:24px;">newnoteformview</div>'
});

```

- ลบ css style ออก

```css
/* app/desktop/src/view/newnoteform/NewnoteformView.scss */

.newnoteformview {
  /* padding: 10px;
  box-shadow: 2px 2px 8px 0 rgba(0, 0, 0, 0.4); */
}
```

บันทึกไฟล์ และทดสอบดูผล