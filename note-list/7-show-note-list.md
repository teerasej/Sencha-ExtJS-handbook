
# แสดง Note List

```js
// app/desktop/src/view/notelist/NotelistView.js

Ext.define('CounterApp.view.notelist.NotelistView',{
	xtype: 'notelistview',
	cls: 'notelistview',
	controller: {type: 'notelistviewcontroller'},
	viewModel: {type: 'notelistviewmodel'},
	requires: [],
	extend: 'Ext.Container',

    // แสดง list component
	items: [
		{
			xtype: 'list',

            // กำหนด item template
            // ดึง property message ของ object จากแหล่งข้อมูลมาแสดง
			itemTpl: '{message}',

            // กำหนด array 1 ชุด เป็นแหล่งข้อมูลผ่าน data property
			data: [
				{ message: 'a' },
				{ message: 'b' },
				{ message: 'c' },
			]
		}
	]
});

```

บันทึก และทดสอบผล