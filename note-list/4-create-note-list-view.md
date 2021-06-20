
# สร้าง Note List View และเอามาใช้ใน Main View

## 1. คำสั่งสร้าง View Package

เปิด Terminal ขึ้นมาภายในโฟลเดอร์ของโปรเจค และรันคำสั่ง

```
ext-build generate viewpackage desktop notelist
```

นำ notelist มาใช้ใน MainView.js

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
    {
      xtype: 'panel',
      width: 600,
      height: 450,
      title: 'Note List',
      shadow: 'true',
      padding: 10,

      // กำหนด layout เป็น hbox
      layout: 'hbox',
      items: [
        {
          xtype: 'newnoteformview',

          // แบ่งอัตราส่วนกับ component อื่นที่อยู่ใน Container เดียวกัน
          flex: 1
        },
        {
          // เรียกใช้ notelistview
          xtype: 'notelistview',
          // แบ่งอัตราส่วนกับ component อื่นที่อยู่ใน Container เดียวกัน
          flex: 1
        }
      ]
    }
  ]
})

```


## 2. ปรับให้ notelistview เป็น container และปิด styling

```js
// app/desktop/src/view/notelist/NotelistView.js

Ext.define('CounterApp.view.notelist.NotelistView',{
	xtype: 'notelistview',
	cls: 'notelistview',
	controller: {type: 'notelistviewcontroller'},
	viewModel: {type: 'notelistviewmodel'},
	requires: [],

    // เปลี่ยนเป็น Container
	extend: 'Ext.Container',

	html: '<div style="font-size:24px;">notelistview</div>'
});


```

- ลบ css style ออก

```css
/* app/desktop/src/view/notelist/NotelistView.scss */

.notelistview {
  /* padding: 10px;
  box-shadow: 2px 2px 8px 0 rgba(0, 0, 0, 0.4); */
}
```

บันทึกไฟล์ และทดสอบดูผล