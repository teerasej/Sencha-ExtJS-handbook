
# Form validation

ในที่นี้เราจะทำการดึงข้อมูลออกมาจาก form และทำการเช็คความถูกต้อง รวมถึงการใส่ error กลับไปที่

```js
// app/desktop/src/view/newnoteform/NewnoteformViewController.js

Ext.define('CounterApp.view.newnoteform.NewnoteformViewController', {
	extend: 'Ext.app.ViewController',
	alias: 'controller.newnoteformviewcontroller',


	addNewNote: function() {
		console.log('save')
        
        // สร้าง error object
		var errors = {};

        // function getView() เป็นการดึง instance ของ View ที่กำหนดทำงานกับ Controller ตัวนี้มาใช้งาน
		let form = this.getView()

        // ใน form panel เราสามารถใช้ function lookupName() โดยระบุ name ของ field ที่ต้องการ เพื่อเข้าถึง และเอาค่ามาใช้งานได้
		let newNoteMessage = form.lookupName('newNoteMessage').getValue() || ''
		
        // ทำการเช็คข้อความ
		if(newNoteMessage.length === 0) {

            // กำหนด property ให้ errors object ตาม name ของ field
			errors.newNoteMessage = ['เว้นว่างไม่ได้นะ']

            // set error ให้ form
            form.setErrors(errors)
            return
		}

		
	}
});

```

บันทึกและทดสอบการทำงาน

ตรงจุดนี้สามารถลอง[เพิ่มการ debug ตัวแอพ](../kb/setup-vscode-debugger.md)ได้ถ้าต้องการ