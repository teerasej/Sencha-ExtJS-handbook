
# สร้างแบบฟอร์ม

## 1. เปลี่ยน Component NewnoteformView เป็น form panel 

```js
// app/desktop/src/view/newnoteform/NewnoteformView.js

Ext.define('CounterApp.view.newnoteform.NewnoteformView',{
	xtype: 'newnoteformview',
	cls: 'newnoteformview',
	controller: {type: 'newnoteformviewcontroller'},
	viewModel: {type: 'newnoteformviewmodel'},
	requires: [],

    // เปลี่ยนจาก Container เป็น form panel
	extend: 'Ext.form.Panel',

	items: [
        // แสดง text field
		{
			xtype: 'textfield',
			label:'New Note Message',

            // กำหนด name attribute
			name: 'newNoteMessage'
		}
	],

    // form panel จะมี property buttons ให้เพิ่มปุ่มลงไปใน component ได้
    buttons: [

        // กำหนดข้อความ และชื่อ function ที่จะทำงานเมื่อกดปุ่ม
		{
			text: 'Add',
			handler: 'addNewNote'
		}
	]
	
});

```

## 2. สร้าง function ใน ViewController 

```js
// app/desktop/src/view/newnoteform/NewnoteformViewController.js

Ext.define('CounterApp.view.newnoteform.NewnoteformViewController', {
	extend: 'Ext.app.ViewController',
	alias: 'controller.newnoteformviewcontroller',

    // สร้าง function ที่จะถูกเรียกใช้จาก View 
	addNewNote: function() {
		console.log('save')
	}
});

```

บันทึก และทดสอบผล