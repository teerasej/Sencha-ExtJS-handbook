

# เพิ่มข้อมูลลง Store จาก New Note Form

## 1. เพิ่ม reference ให้ textfield property 

เพื่อให้สามารถเรียกใช้จาก ViewController ได้โดยตรง

```js
// app/desktop/src/view/newnoteform/NewnoteformView.js

Ext.define('CounterApp.view.newnoteform.NewnoteformView',{
	xtype: 'newnoteformview',
	cls: 'newnoteformview',
	controller: {type: 'newnoteformviewcontroller'},
	viewModel: {type: 'newnoteformviewmodel'},
	requires: [],
	extend: 'Ext.form.Panel',

	items: [
		{
			xtype: 'textfield',
			label:'New Note Message',
			name: 'newNoteMessage',

            // การตั้ง reference จะคล้ายการตั้ง id ใน html จะทำให้ ViewController สามารถเข้าถึง Component ได้โดยตรง
			reference: 'newNoteMessageBox'
		}
	],

	buttons: [
		{
			text: 'Add',
			handler: 'addNewNote'
		}
	]
	
});

```

## 2. บันทึกข้อความลง store 

- ปรับปรุงการแสดง error - เรียกใช้งาน store ด้วย getStore ผ่าน storeId ที่ตั้งไว้ - เข้าถึง textfield ผ่านชื่อ reference - เคลียร์ข้อความใน textfield

```js
// app/desktop/src/view/newnoteform/NewnoteformViewController.js

Ext.define('CounterApp.view.newnoteform.NewnoteformViewController', {
	extend: 'Ext.app.ViewController',
	alias: 'controller.newnoteformviewcontroller',


	addNewNote: function() {
		console.log('save')

		var errors = {};

		let form = this.getView()
		let newNoteMessage = form.lookupName('newNoteMessage').getValue() || ''
		
		if(newNoteMessage.length === 0) {
			errors.newNoteMessage = ['เว้นว่างไม่ได้นะ']
			form.setErrors(errors)
			return;
		}

        // เรียกใช้งาน store จาก function Ext.getStore() โดยระบุ storeId
		var store = Ext.getStore('notes')

        // เพิ่ม object ที่มี property message เข้าไปใน store
		store.add({ message: newNoteMessage })
		
        // ใช้ function this.lookupReference() เพื่อเข้าถึง component โดยตรงจาก View
        // ให้ระบุชื่อ reference ที่ตั้งไว้
		let newNoteMessageBox = this.lookupReference('newNoteMessageBox')
		newNoteMessageBox.reset()
	}
});

```

บันทึกไฟล์ และทดสอบผล